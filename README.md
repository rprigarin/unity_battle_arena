# Unity MOBA experiment
A small MOBA proof of concept written in Unity.


## About


This is a game written by me for a friend's project starting from around the winter of 2022, with the most significant changes and features added during summer of that year.  

It started as basis for the idea of extending MOBA gameplay features using Unity into a whole new game, more specifically a singleplayer experience with ability customization and tag-based teams. This project presents what we have achieved thus far during our endeavor.  

A lot of inspiration was taken in particular from League of Legends (aka. LoL or League for short), such as ability interactions, combos, auto-attack kiting, ability buffering, and how the player state is influenced as a result of casting these abilities. Keeping tracks of these interactions provided a lot of insight on how they would have to be considered just from analysing how League approached it (more or less consistently), resulting in trying to create some underlying systems for our project.  

Making the systems that are both consistent and scalable (i.e., allows for integration of many more playable characters with very different ability interactions) ended up being one of the biggest challenges faced in this project, and while it was indeed challenging, it proved to be a lot of fun trying to work with it and coming up with different methods for solving it within Unity's framework.


## Controls


The game is based on League of Legends and thus shares a lot of the same controls.


### General controls


* **Right Mouse Button**	- makes the player character move to the clicked location or target an enemy. If targeting an enemy and that enemy is within the player's attack range, the player character will start launching basic attacks (melee or ranged) at an interval, until the enemy dies or the player clicks elsewhere

* **A + Left Mouse Button**		- targets an enemy closest to the mouse cursor. This is similar to the attack on move bind from LoL, often utilised by ranged champions  

* **Q/W/E/R**	- player character's abilities corresponding to each key

* **Y**			- attach/detach the camera  
* **Space**		- centers the camera (if detached)  

> **Note**: If the camera is detached, the camera stays in place where it was detached. It becomes separate from the player character, and can be controlled by moving the mouse to the edges of the screen  

* **Esc**		- exits the game


### Champion-specific controls

This section elaborates on the abilities each of the characters support in the game:


#### Player  

The player is a ranged character and thus their basic attacks trigger from a further distance.

* **Q** - Casts a projectile in a straight line. If the projectile is empowered and hits an enemy, the cooldown is reset  
* **W** - Empowers the Q projectile. Can be toggled on/off  
* **E** - The player performs a dash to the direction of the mouse cursor  
* **R** - Unassigned  


#### Pyke

Pyke is a melee champion from League of Legends. The abilities are more or less based on how they perform in the actual game.  
> **Note**: While there are no animations of visuals for melee basic attacks being performed, they do in fact trigger and deal damage whenever you target enemies  

The abilities go as follows:  

* **Q** - Pyke jabs his dagger in a straight line. If Q is held, it turns into a hook that has longer range. If the hook catches an enemy, they are dragged towards Pyke then briefly slowed  
* **W** - Pyke gains increased movement speed that decays over time. Casting another ability cancels the movement speed bonus  
* **E** - Pyke dashes forward and leaves a phantom, which then follows Pyke and damages enemies that come in contact along its path  
* **R** - Pyke strikes a target from range, teleporting to their location. If the enemy is killed by this ability, its cooldown resets and it can be recast for a brief period  


## Issues


Because I was writing this project while concurrently learning about better programming practices and how to use Unity, there are some glaring issues with the code that should be pointed out:  
* redundant code
* haphazardly-implemented event-driven programming
* hard-coded parameters
* no tests

Redundant code currently exists as a result of creating Pyke by duplicating all the player code. It is a temporary attempt at implementing multiple characters in the game to see how the underlying systems can accommodate them.

It wasn't until sometime in 2022 that I learned about event-driven programming, and before then utilised a lot of polling and substitutes for events by creating classes with boolean flags acting like "events." I was basically trying out different ways to communicate information between game objects, but had I known event-driven features of C# from start I would have used that where I could for efficiency reasons.

A lot of hard-coded parameters exist for some of the underlying logic of projectiles and crowd control effects, such as interactions with Pyke's hook. A more elegant method of applying these values would have to be designed.

I would like to write tests at some point to ensure game functionality, especially with something as volatile as making a MOBA.


## Credits


All creative rights for the original gameplay mechanics of Pyke belong to Riot Games.  
This project is written and maintained by Ruslan Prigarin.

