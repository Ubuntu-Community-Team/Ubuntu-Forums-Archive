---
title: "Party Light Show with Linux"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by arigram on 2007-12-10
The holidays are almost upon us and parties are being busily cooked!
...or they should be!

Craving to fill a deep psychological need from childhood, recently I felt the urge to transform my living room/photography studio into a groovy bona fide disco party experience!

There are disco balls with motors, spotlights with rotating filters, "laser" LED spotlights for beam and pattern effects, oil lamp projectors, black lights, strobes, smoke and bubble machines and all that controlled by switches, remote controls and sound activators.

At the same time you have some good Linux music players with well designed list interfaces, party full screen modes and some ok (but not that good) visualisations.

Is there a way to bring all this together?
Somehow control the light show in the same way one controls the music?

If there isn't, someone must get busy! There is huge potential here!

---

### Post by FuzzyTheBear on 2007-12-10
There's very little in the way of controllers for lighting that 
dosent need a controller ! .. and that's where it starts and stops 
mostly.All the pro lighting fixtures may be addressed with a DMX 512 or so 
protocol / controller .. but you need the hardware to do it.
Hardware is the hard part . Each device would need to be DMX addressable
and daisy chain plugged in a controller/card .
If they are , you need to check with reputable manufacturers like 
strand for software and controllers. 
Again .. this is not that it cant be done .. it already does.
Its a matter of getting the dmx controller/software/light board
and dimmer packs.

once you have the hardware , there's virtual lighting consoles 
for Linux free on the net.Mileage may vary.
 
Check also the linux laser project for some great hacks

[http://www.linux-laser.org/](http://www.linux-laser.org/)
also 
[http://llg.cubic.org/](http://llg.cubic.org/)      <dmx4lin drivers 

check out the other links .. might give you ideas

---

### Post by FuzzyTheBear on 2007-12-10
what im trying to say is this .  
( now i got my coffee .. so i can take the time :) 

the machines you try to control need some kind of interface.
may it be relays , rs-232 dmx or even infrared.
to deal with all these different methods a general purpose 
controller ( think crestron or amx box with a bunch of different control
lines in multiple formats relays i/o lines rs-232 ir etc  ) 
might be more adequate.

make a good description of the fixtures , the ways they are controlled
what you truly want to do with them. 

Maybe the solution already exists and it's not worth reinventing the wheel..
but then again .. this may be a fun weekend project for hardware hackers
to come up with novelty relay boards for a pci bus  etc .. banks of relays controlled wiht rs-232 etc .

Give us more details :) 

Fuzz

---

### Post by arigram on 2007-12-10
Give you more details Fuzz?

Man, I had to go carefully over your words to make sure I read them right,
for I am but an  Ubuntu n00b with very little hax0r experience and
just a tiny bit desire to party especially before I get too old.

What you pointed out was very interesting though.

At the simplest stage, one would need a connector board,
where all the equipment will be attached too (hard or plug),
which in turn will transfer their signals to the computer
either via USB or PCI.
Such cards exist for Arcade cabinet and Simulator cockpit
control for all the buttons, lights, levers, instruments and displays
and this what I am thinking of.

So, at the simplest stage you have binary control, on and off of the
equipment. Not a little thing as you would be able to turn on and off
certain equipment when desired and even script them to timing
or music. Next stage would be to control their other switches, such
as turning on their sound activator, or their motor and its direction. 
Simple binary control as well, just more of it. 
Something like that even I could hook up with some soldering
iron. And so on for more refined control.

It doesn't have to be a controller of multi-thousand laser devices.
A room can be groovy enough with 50-100 euro toys with lots
of blinking lights and rotating motors. Having a means to control
all of them via the computer where you can even tie them to a
music player means that you get to control their cumulative power.
(suddenly I feel like I am taking baby steps from a party dude to an evil genius).

So, let's say you have a board with ten hooks on it, connected to the computer
with a USB cable and controlled via a simple GUI, maybe a plug-in inside one
of the popular music players.
You connect the board to the on/off switches of a disco ball motor, a spotlight
with colored filters, a smoke machine, a strobo light, a LED pattern machine, etc
and you can turn them on and off when desired, combine them how you like
or script them so you can go dance with the girls and not sit in front of the screen.

So, you can call it a simple lights switch and I am sure something like that exists.
It was trendy a decade ago at least.

(disclaimer: I have almost no programming or hard-hacking experience)

---

### Post by FuzzyTheBear on 2007-12-11
well   lo and behold .. if we're talking off the shelf and not
pro light devices like robo-scans and the likes .. our life 
just became a lot easier . One of my colleagues last week 
did a rs-232 to relay converter , which is a good start .. if you 
got rs-232 .. ill try to get the schematic later this week when 
i see him.

We did have what we called then a color organ : 
simple bunch of scr's and filters for the different sound
bands , quite easy to recreate. it would be plugged in the 
preamp and would activate 110 v ac lights to the sound of 
music. again , the same basic principle can be of use for
some of the controlling.
 
We can use a low freq filter / detector to " forward " a bunch of 
relays to make lights " change " to the beat etc.

Again , we can probably easily make " scenes " that are changing
with the beat detection / manually .

Euro devices make me beleive you're dealing with 220 V 

PS : i make my living in professional a/v controllers , so
for me this is an interresting project. i mostly write the software
and touch panels for them.So i might take this a bit over the edge
which is hwy i need parameters to keep it simple  :D 

What is your level of proficiency in hardware ? 
if i make pc board drawings , are you able to reproduce those 
and assemble some kit ? 

Ric

---

### Post by FuzzyTheBear on 2007-12-11
ok .. last post for the morning : 

ill tell you what my real secret is : 

i been wanting to make a full control system , totally open source
hard and soft for a whole house system.party room included.
i seen a linux distro for A/V control and playback and since then i been 
dreaming of taking the whole shoebang to a whole new level .
adding the control hardware for rs-232 , relay and i/o sensors 
to make this a complete a/v whole house package.

A bit like i do with amx and crestron hardware at work but full open source.

check this : [http://video.google.com/videoplay?docid=2176025602905109829&hl=en](http://video.google.com/videoplay?docid=2176025602905109829&hl=en)

it's about LinuxMCE 

party room would be a simple sub-system in the whole concept.

---

