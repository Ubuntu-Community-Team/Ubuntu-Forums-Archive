---
title: "Nvidia GTX 480, 6 Cores amd processor: can't run blu-ray videos and 1080p videos"
date: 2011-02-05
forum: Multimedia Software
---

### Post by XMasterrrr on 2011-02-05
hello guys,

first i'm glad to join this community i have been windows user for 6 years and finally i just leave it and get to work on ubuntu(linux) so, i leaved windows as i think for ever as i'm a programmer who thinking in Kernel programming>>>

i found a problem that i had been searching for a solve for more than 3 days

blu-ray and HD 1080p videos are so lag i can't see a 3 seconds then it lag

my specifications are fine and more than fine as i think

any way to fix this ?

thank's :)

---

### Post by cchhrriiss121212 on 2011-02-05
Have you installed the recommended driver from System>Admin>Hardware Drivers?
Have you tried using vdpau output in smplayer?

---

### Post by XMasterrrr on 2011-02-06
the driver already installed

i got it work with mplayer and vdpau but i can't trick the smplayer out 

so can you help me maybe this fix it up

---

### Post by cchhrriiss121212 on 2011-02-06
> 
i got it work with mplayer and vdpau but i can't trick the smplayer out 
Could you explain this a little more? You select video output from the preferences>video menu. If something does not work the way you want, be specific about what happened.

When you had vdpau working with mplayer, did it give acceptable performance?

---

### Post by XMasterrrr on 2011-02-08
iam sorry for been late on answering you

i'll do it tomorrow and answer you then

---

### Post by XMasterrrr on 2011-02-09
ok so i used this : 

```
 			 				$mplayer -vo vdpau -vc ffh264vdpau path/to/file 			 		
```

it worked with some times lag some times video tearing 

i don't know why , when i was using windows it never happens like this :S

i want an answer please :S

thank's in advice

---

### Post by BicyclerBoy on 2011-02-10
The tearing is most likely to do with the "sync to vertical blanking" is not set for this screen.
Have a look in the nvidia-settings GUI program..
"X server XVideo settings"

If you have multiple displays using separate X screens then this setting has to be set for each screen displaying video..

The other cause is compiz effects...AFAIK this has a vsync-blank setting hidden somewhere.

You need a really long cmd line option to get the best out of mplayer...hard work.

What video driver are you using 260 or 270 ?

---

### Post by XMasterrrr on 2011-02-10
> **BicyclerBoy said:**
> The tearing is most likely to do with the "sync to vertical blanking" is not set for this screen.
Have a look in the nvidia-settings GUI program..
"X server XVideo settings"

If you have multiple displays using separate X screens then this setting has to be set for each screen displaying video..

The other cause is compiz effects...AFAIK this has a vsync-blank setting hidden somewhere.

You need a really long cmd line option to get the best out of mplayer...hard work.

What video driver are you using 260 or 270 ?

so in "X server XVideo settings" i'll just make it false on the sync vblank right?

iam using single display

and how to stop the compiz to get it stop ?

and the driver are 270.18

---

### Post by BicyclerBoy on 2011-02-10
Should be set/ticked/true for sync vertical blank (XVideo).

I have a suspicion that vdpau playback uses it's own internal vsync..

Are you using mplayer -vo vdpau ?

You can disable compiz under System/Preferences/Appearance/Visual Effects  [none].

Compiz & vdpau video & two X screens H264/1080 works fine for me...

Other things to try:
  sudo nvidia-xconfig --no-composite

or with the following lines in /etc/X11/xorg.conf:

   Section "Extensions"
       Option "Composite" "Disable"
   EndSection


GPU power scaling:
set it to max performance & see if problem goes away..

vdpau buffers.
set vdpaubuffersize=32 or higher

---

### Post by BicyclerBoy on 2011-02-11
From some other thread..about compiz & tearing video.

Compiz Settings Manager (You need to install it from the repo)
General Options > General
check the box "Undirected  Fullscreen Window"

---

### Post by XMasterrrr on 2011-02-14
thank you i think it's good now

but how can i use smplayer instead of mplayer ?

with the same previous command

---

