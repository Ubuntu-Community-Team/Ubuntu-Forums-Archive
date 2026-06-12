---
title: "Call for testing: multitouch gestures in unity"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by lamalex on 2011-04-01
Call For Testing: Multitouch

Do you have multitouch hardware? A macbook with multitouch track pad? A magic mouse? A super fancy touch screen laptop? Do you want to help ensure users have an amazing and exhilarating multitouch experience?

We are looking for volunteers to test Unity's multitouch functionality. The goal of this testing is to catch, and fix bugs before they reach a major audience.

If you want to be part of the team you will need:

 1. A computer with some kind of multitouch hardware.
 2. A computer than can run Unity
 3. An Internet connection

If you want to take part in this adventure, go to:
  [https://wiki.ubuntu.com/Unity/Testing/Multitouch](https://wiki.ubuntu.com/Unity/Testing/Multitouch)
and follow the detailed instructions.

Thanks for helping making Ubuntu even better!

---

### Post by MacUntu on 2011-04-01
Do we need to install any packages for this to work? My Synaptics touchpad just moves the window in the background on a three finger tap on the window border (simulate double click).

---

### Post by lamalex on 2011-04-01
The utouch packages are required, but they should be pulled in along with unity. There should be a geistest binary that will tell you how utouch is registering your presses. The geistest binary comes with utouch-geis-tools package, which i honestly forget if that's installed by default or a package i installed.

---

### Post by MacUntu on 2011-04-01
That's all I get for three finger taps (tap/pinch/drag gestures):

```
Device 10 added
	attr "device name" = "SynPS/2 Synaptics TouchPad"
	attr "device id" = 10
	attr "direct touch" = false
	attr "independent touch" = false
	attr "device touches" = 4
	attr "Abs MT Position X 0 min" = 1472.000000
	attr "Abs MT Position X 0 max" = 5888.000000
	attr "Abs MT Position X 0 resolution" = 0
	attr "Abs MT Position Y 1 min" = 1408.000000
	attr "Abs MT Position Y 1 max" = 4820.000000
	attr "Abs MT Position Y 1 resolution" = 0
	attr "Abs MT Tracking ID 2 min" = 0.000000
	attr "Abs MT Tracking ID 2 max" = 65535.000000
	attr "Abs MT Tracking ID 2 resolution" = 0
Gesture id 804 type 15 updated
	attr "device id" = 10
	attr "timestamp" = 7761270
	attr "root window id" = 181
	attr "event window id" = 33554470
	attr "child window id" = 33554470
	attr "focus x" = 1120.000000
	attr "focus y" = 384.000000
	attr "gesture name" = "Tap,touch=2"
	attr "touches" = 2
	attr "tap time" = 100.000000
	attr "position x" = 546.558044
	attr "position y" = 201.260254
	attr "boundingbox x1" = 322.826111
	attr "boundingbox y1" = -24.794861
	attr "boundingbox x2" = 770.289856
	attr "boundingbox y2" = 427.315308
	attr "touch 0 id" = 3303.000000
	attr "touch 0 x" = 322.826111
	attr "touch 0 y" = 427.315308
	attr "touch 1 id" = 3304.000000
	attr "touch 1 x" = 770.289856
	attr "touch 1 y" = -24.794861
```

Guess the device is of no use then (it's a touchpad in a ThinkPad T510)?

---

### Post by ninjaaron on 2011-04-01
I have a Dell Inspiron Duo with an eGalax multitouch screen, but xinput doesn't recognize it properly, and I haven't a clue how to reconfigure it.

:-x

---

### Post by meanpt on 2011-04-02
HP TouchSmart tm2 core i3 380UM 1.33 Ghz
Would like to help but, unfortunately, I've not been able to even start a live session due to unsupported graphics hardware out of the beta1 DVD.

Graphics cards:
Ati Mobility Radeon 5450
Intel(R) HD Graphics
Wireless Card
Broadcom 4313 802.11b/g/n
Touch Devices
Synaptics ClickPad V7.4
Wacom device (pen)
TouchScreen (can't find much more about this)

---

### Post by Favux on 2011-04-02
Hi meanpt,

It's a Wacom 2 finger touch screen sandwiched with the Wacom digitizer.  Both connect through USB.

---

### Post by meanpt on 2011-04-03
Thanks, Favux.Going to add that info on my hardinfo profile file.My testing resources are not so bad at all and yet I can't "touch" ubuntu outside a virtual machine. :(

---

### Post by Bufke on 2011-04-03
My touch screen supports only 2 fingers. geistest works, but all these command require at least 3 fingers. Is there anything I can do with 2? Or remap them somehow? Using a Lenovo S10-3t.

---

### Post by lamalex on 2011-04-05
The list of supported hardware is available at, [https://wiki.ubuntu.com/Multitouch/HardwareSupport](https://wiki.ubuntu.com/Multitouch/HardwareSupport). If you don't have one of those devices, unfortunately there's not much you can help with on this initiative, but we appreciate the enthusiasm!

---

### Post by Favux on 2011-04-05
Hi lamalex,

I'd like to point out two of the five new Wacom Bamboo Pen and Touch tablets (released Oct. 2010) are called Special Editions.  And they have 3 and 4 finger touch.  Since the xf86-input-wacom driver will never support more than two finger touch (and the current gestures) they need multi-touch support from the Ubuntu Utouch stack.  Synaptic or evdev for touch?

---

### Post by xzero1 on 2011-04-05
I would be willing to test it on a MSI Windtop AE2220 but since the sound does not work on this machine and the devs seem to be unwilling to fix that, it would just be a waste of time.:(

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/664189]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/664189")

---

### Post by cariboo on 2011-04-05
If you have a complaint about how bugs are fixed, this isn't the place to voice it. Have you tried the ubuntu-devel mailing list?

---

### Post by ElSlunko on 2011-04-05
I'd love to help but my HP dm4 is not supported. I'll keep looking to see if it becomes available.

---

### Post by xzero1 on 2011-04-06
> **cariboo907 said:**
> If you have a complaint about how bugs are fixed, this isn't the place to voice it. Have you tried the ubuntu-devel mailing list?

It is not my pc and I don't have the access to it I would like. It just seems that after filing the bug report, it was essentially ignored. Why should I waste any more time on it? As far as complaints, should they be filed in secret or in public so that people know about them? I thought Ubuntu was a community driven project.

---

### Post by cariboo on 2011-04-06
> **xzero1 said:**
> It is not my pc and I don't have the access to it I would like. It just seems that after filing the bug report, it was essentially ignored. Why should I waste any more time on it? As far as complaints, should they be filed in secret or in public so that people know about them? I thought Ubuntu was a community driven project.

This isn't the place to complain, because normally the developers don't read the forums, because of all the excessive noise, they look at specific topics, but not any of the general threads. The mailing lists are also open to anyone, so they aren't private in the least.

---

### Post by andrek on 2011-04-07
I've got a problem. My setup is definitely multitouch capable (two-fingers scrolling, three fingers as a middle click) yet nothing happens when i use three fingers on a window (which would move it). Is there any package that I'm missing?
I'm running Unity, obviously.
/edit
Uh, oh, is this supposed to work on Synaptics touchpads?

---

### Post by MacUntu on 2011-04-07
Maybe bug, maybe unsupported, maybe something else. :)

[http://askubuntu.com/questions/33574/how-can-i-test-to-see-if-my-touchpad-is-supports-more-than-2-finger-gestures/33589#33589](http://askubuntu.com/questions/33574/how-can-i-test-to-see-if-my-touchpad-is-supports-more-than-2-finger-gestures/33589#33589)

---

### Post by andrek on 2011-04-07
Thanks, I'm seeing the same on my dell studio 1555 so looks like it's up to uTouch or Synaptics, not some specific laptop model.

---

### Post by wersdaluv on 2011-04-10
I'm trying it on my MacBook Air 3,1 (11" late 2010).

I installed **utouch** and three finger gestures don't respond. Running **geistest** on terminal gives no output too. Also trying to enable "Toggle Handles" on CCSM, but I dunno how it would react to multitouch.

---

### Post by smallblackanimal on 2011-04-12
Just tested 32bit live cd on my dell studio 1749. 3 finger tap gesture brings up window "handles" and resizing and window moving work fine. 4 finger tap generates the shortcut launcher. That was as much as I was able to accomplish since I'm having a problem with random mouse cursor movement and clicks. I had a similar problem with 10.10 that was fixed with a synaptics driver update in Win7. right now I'm not sure if its a issue with running from live cd and updates are needed or if there's something else. 

I could not get 2 finger drag/scrolling - 3 finger pinch/maximize-restore -or  4 finger drag/switch workspace to work (probably do to the mouse problem I expect). I plan on downloading 64 bit beta 2 to install on a test partition later this week for a better evaluation. 

I also took a quick look at /usr/share/ginn/Wishes.xml and if I remember correctly some of the shortcuts are wrong. <super><e> for expo/workspace switcher when in unity the default is <super><s>.

---

### Post by DogMatix on 2011-04-13
I have a Wacom Bamboo Pen & Touch that I connected to an Acer Aspire One 5031h netbook running (at time of posting) 11.04 beta2 & it seems to be functional without any intervention. 

**Side note:** Kills the battery life though.

---

### Post by DanaG on 2011-04-14
I'd test multitouch gestures... but first I need somebody to give my touchpad multifinger detection in Linux: 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/546697](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/546697)

EDIT: Also, I have a Magic Trackpad that I don't use.
If anything, my ideal behavior would be a non-sucky variant of the Windows ClickPads.

The ClickPads let you press left+right edges of bottom to get a middle-click... and you can even middle-drag.


EDIT: Just tried the Magic Trackpad.  
Vertical 2-finger scroll: works.
Vertical edge scroll: works.  And yes, I absolutely want both.
Horizontal: neither edge nor 2-finger.

3-finger drag: drags window.
4-finger drag: does nothing.

Pinch gesture: does nothing.
2-finger tap or physical click is middle-click.
3-finger is nothing at all.
4-finger is Unity menu.... but what's right-click?  Er....
5-finger (wow!) is right-click.

EDIT: Also, for some reason the drag handles don't appear.

Frankly, I don't like the tapping... the Magic Trackpad's insanely high sensitivity makes normal Synaptics touchpads seem quite tame.

Also, the normal mouse movement is too darn slow, but my built-in touchpad is fine.  How do I make just the Magic Trackpad faster?

---

### Post by rubengs on 2011-04-15
I made all the tests and submitted the results, everything worked ok in magic track pad except the maximized window procedure that involves a two finger scrolling. 

In another set of things I think is great to have a complete multitouch experience in Natty, but I have a sensible problem, at least for me, I desperately need to use the three finger tap to simulate the mouse middle click button, and need to drag with three fingers as well, I use it to drag text to search zones in firefox and other programs. The three finger middle click is very useful to close open tabs and to open links in new tabs in firefox, to open directories in tabs in nautilus, to close windows in the scale plugin in compiz, etc. 

How can I assign another gesture other than three finger tap/drag to mouse moving resizing and take back this to the previous behavior?

---

### Post by bregma on 2011-04-23
For the record, most Synaptics touchpads are what we call "semi-multitouch".  They are not true multi-touch devices because they do not report actual touches, only the "bounding box" surrounding where your fingers are.  Because of this, they are incapable of reporting gestures with more than 2 fingers or even 2-finger rotations.

The three-finger tap is reported by the hardware as a button event, not a three-finger touch.

These touchpads are still useful for two-finger pinch, tap, or drag gestures, but alternative keystrokes are necessary for using them with Unity.

---

### Post by DanaG on 2011-04-23
Speaking of multi-finger detection on Synaptics, what do I need to do to get somebody to look at this issue?
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/546697](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/546697)
All the responses I've ever gotten seem to be "pffft, it's impossible for a driver to give it multifinger detection if it didn't already have it".  (To which I say: What, can drivers not load firmware to devices?  Fine, then delete /lib/firmware, and see how well your devices work when drivers can't load firmware!)

---

