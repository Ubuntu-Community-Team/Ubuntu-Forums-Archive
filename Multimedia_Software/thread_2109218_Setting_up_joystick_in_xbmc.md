---
title: "Setting up joystick in xbmc"
date: 2013-01-26
forum: Multimedia Software
---

### Post by whocares02 on 2013-01-26
Can somebody help me setting up my joystick in xbmc?

I found guides on the net but they are pretty bad written (see [here]("http://wiki.xbmc.org/index.php?title=Keymap") and [here]("http://lektiondestages.blogspot.de/2013/01/using-usb-joystick-or-gamepad-in-xbmc.html")).

 I know I have to edit the file ~/.xbmc/userdata/keymaps/Keymap.xml 

Inside the file I add a new tag inside the global-tag called

```
<joystick name="NAME_OF_YOUR_JOYSTICK"> </joystick>
```[FONT=&quot]

The name of the joystick I get with 

[/FONT]```
 cat /proc/bus/input/devices
```[FONT=&quot]

Okay, so far so good. But how do I define the directions?

The 2nd guide reads:
[/FONT]> 
for an axis add:
*<axis id="AXIS_ID" limit="VALUE_LIMIT">NAME_OF_XBMC_ACTION</axis>*
and for a D-PAD or hat add:
*<had id="HAT_ID" position="DIRECTION">"NAME_OF_XBMC_ACTION</hat>*

*BUTTON_ID*, *AXIS_ID* and *HAT_ID* correspond to the index you got from *jstest* above **+1**, as *jstest*s indices start as 0, but XBMC seems to start from 1...
*VALUE_LIMIT *is the limit that needs to be reached so XBMC  activates that function. The default value of an axis is usually 0, so  use "+1" and "-1" for the different directions of the axis.
*DIRECTION* is the direction of the D-PAD or hat and takes strings like "left", "right", "up" or "down".With the command jstest I can see the left-right-movement of the left mini-joystick on my gamepad (it looks like a playstation-2-gamepad) is axis 0. Unfortunately the values are negative when I move it left and positiv when moving right. So what do I use to fill-in the field reading "value-limit"? 

Jstest is using values from -32767 to -1 for left-movement and 1-32767 for right-movement. Jscal is using values from 0-127 for left and 129-255 for right-movement.
128 is middle-position when not touching anything. Which numbers do I have to use for the Keymap.xml?
Guide number one doesn't explain anything at all.

---

### Post by whocares02 on 2013-01-26
I now tried this line in Keymap.xml but xbmc is just not reacting on any movement:

```
    <joystick name="Mega World USB Game Controllers">
       <axis id="0" limit="-1">Left</axis>
       <axis id="0" limit="1">Right</axis>       
    </joystick>
```

---

### Post by whocares02 on 2013-07-11
Is it possible only certain joysticks (xbox, wii, ps3) are supported by xbmc? The [wiki-page about xbmc's event-server]("http://wiki.xbmc.org/?title=EventServer") is so confusing. First it reads something about joystick-setup in general. At the end it lists a few supported devices.

Can I use my standard-joystick or not?

---

### Post by whocares02 on 2013-07-12
Finally I got it to work. Thanks to [this blog-post]("http://lektiondestages.blogspot.de/2013/01/using-usb-joystick-or-gamepad-in-xbmc.html") I found out that the joypad's d-pad is actually reacting on this line:

```
<hat id="1" direction="left">Left</hat>
```

Hence the joystick-part in Keymap.xml has to look something like this:

```
<keymap>
     <global>
          <joystick name="Mega World USB Game Controllers">
          <axis id="1" limit="-1">Left</axis>      <!-- Left analogue-stick turning left (giving negative numbers) -->
          <axis id="1" limit="1">Right</axis>       <!-- Left analogue-stick turning right (returning positive numbers) -->
          <axis id="2" limit="-1">Up</axis>       <!-- Left analogue-stick turning up (giving negative numbers) -->
          <axis id="2" limit="1">Down</axis>       <!-- Left analogue-stick turning down (giving positive numbers) -->

          <hat id="1" direction="left">Left</hat>
          <hat id="1" direction="right">Right</hat>
          <hat id="1" direction="up">Up</hat>
          <hat id="1" direction="down">Down</hat>
          
          <button id="1">Back</button>
           <button id="3">Select</button>

      </joystick>
    </global>
</keymap>
```

 Important thing for the axis-stuff is the id. JStest is giving wrong ids. I had to increase all numbers by one because jstest begins to count with 0 and not with 1. Every axis-id is for two directions (Left+Right or Up+Down).  E.G. Id1 in my case is for left and right of the first analogue-stick (jstest is calling it Id0). ID0 doesn't exist in xbmc.

Also important: The hat-id doesn't change with directions and is just always 1 in my case. Instead of numbers xbmc's keymap.xml is really getting the commands up, down left and right, which are not reported by jstest.

 So yes, it is possible to use a standard-joystick.

Hope this will help somebody. I'm dissapointed nobody did help me here. :(

---

