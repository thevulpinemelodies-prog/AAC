# AAC
Automated Animatronic Composer is an advanced Roblox animatronic controller designed to record and play back Commands and synchronized audio.

[Roblox Animatronic Control System]

<img width="797" height="609" alt="image" src="https://github.com/user-attachments/assets/81ea776e-1d35-44e7-a3c2-dd3b24fc5944" />


This script controls animatronics, stage lights, and audio sync in Roblox. It reads binary channels to send commands to the bools.

[System Overview]

Scripts

CharacterController: Handles character movement, hinge logic, and showtape playback.

LightController: Handles light brightness, flashing, and strobes.

KeyBind and Remote: Handles client UI controls and audio resync signals.

It uses CollectionService to find tagged character models. Uses bit Charts to manage command valves and Hinge states.
 
[Setup Guide]

Studio Setup Steps

[Character Controller]
Group all character parts into a single Model or Folder in Roblox Studio.

Place the CharacterController script directly inside the character model.

Inside the script has a folder called "Movements"

It should already include a string value, name that string value to the name of the hinge you want to move

In the attributes section of the string value, you can set the angle and the bit

You are also able to activate head turn and set an opposite angle.

there is also an "Is Prismatic" Bool if activated it will work on prismatic constraints instead of hinges

You might have seen the "Key" value too it should have been set to E by default, but you can make it any key you want it to, it's primarily key bind setting for recording. Other Key is just the opposite key for headturns

Now you have a movement set up, you can duplicate the string value and name it to a different hinge or prismatic to set up another movment

For the "Bit" Value, it's best to refer to a Bit Chart there are many online and there should be some that come with your AAC, they basically tell you what number to set your movement too. for example, Chucks Mouth would be Bit 1 for 3-Stage, so you would set the Bit Value to 1. This is for compatibly with official data, but if you have a custom show, you don't necessarily have to use a Bit Chart, just set the Bit Number to any number you want that movement to fire on, make sure not to have two movements on the same bit number or they will fire at the same time unless that's what your going for. It is best to have your show linked up to official bit standards even if its a custom show, just to have compatibility with official data or other peoples showtapes. ALSO MAKE SURE TO SET TOP OR BOTTOM DRAWER, WITH THE "TOP" Value if the "TOP" Value is true it means topdrawer and if its false it means bottom. you may see top or bottom in the bitcharts you see so make sure its important to set them.

Also, a quick note, you may have noticed under the AAC script there's a folder called "BitCharts" and under it has two drawers Top and Bottom. If you want to add more bits to your show you can go under either drawer and add more BoolValues, just make sure that they are numbered and they don't overlap ever.

[Light Controller]

The Light Controller is practically the same as the Character Controller, but instead you have to set the brightness and different settings.

Dont worry about dissabling the light, the script dose that automatically and doing that will cause it not to work.

So, let's go through the settings. Brightness sets the brightness of the light, Fade Duration sets how fast the light fades in seconds when turning on or off so if its set to 1 it will take one second for the light to get to full brightness while 0 is instant being well 0 seconds. Strobe basically just strobes the light on and off, although it is affected by Fade Duration so lower Fade Duration faster strobe, Flash basically Flashes the light once and it wont Flash again until the bit is turned off and on again. Houselights are basically just a setting for houselights what it dose is invert the bit so when the bit is one it will dim the lights this is connected to the "LowerDim" setting its basically the brightness you want to set for the hosuelights dimming.

[WHAT ARE BITS]

A bit is an on and off value, kind of like a light switch.

When a bit is on it will move that movement to the set angle, and when its off it will return to its original angle.

the same for lights when a bit is on it will set the light to the set brightness and if its off it will go to its original value.

bits can litterally be used for anything because all they are is a switch telling somthing to do somthing, it can be hooked up to tell a part to move to a place, or tell a tv to turn on.

and bit charts is just where it holds all the bits, so you could say each bit represents a switch for that movement or light, and the Number or Name of the bit just connects the movement to that bit.

More advanced bits called DMX aren't like switches unlike bits, DMX holds Values kinda like storage.
DMX often looks like this [0,0,0] - [0,0,0] but other versions can just only have [0,0,0]. and these are great for certain use cases like storing XYZ pos and XYZ rot basically you can be able to precisely control rotation and position and play it back unlike bits which can only turn on and off a predetermined value. DMX can also store other stuff like color values making you able to control the color of certain things. DMX is mostly used in things like moving lights and spotlights, to rotate and move lighting. that is called DMX lighting

Now the Baise AAC does not include DMX it only includes Bits, because DMX is far more storage intensive then a Bit. meaning it is not compatible with the AAC String Data System or SDS, DMX would have to use a Script Timing System or STS, which can hold much more data more compact but at the cost of it being harder to sync.

[Example BitChart]
This bit chart isn't a real bit chart and is a representation of what a bit chart might look like

[TopDrawer]
Arm and Body

Bit 01: Left Arm Raise

Bit 02: Left Arm Twist

Bit 03: Left Elbow

Bit 08: Right Arm Forward

Bit 09: Body Lean

Head and Face

Bit 10: Head Turn

Bit 11: Head Tilt

Bit 12: Mouth Open and Close

Bit 13: Eyelids Down

[BottomDrawer]

Lights and effects

Bit 01: SpotLight Character1

Bit 02: SpotLight Character2

Bit 03: Strobe Light Center

Other characters

Bit 08: BillyBob Right Arm Forward

Bit 09: BillyBob Body Lean

Head and Face

Bit 10: BillyBob Head Turn

Bit 11: BillyBob Head Tilt

Bit 12: BillyBob Mouth

Bit 13: BillyBob Eyelids Down
