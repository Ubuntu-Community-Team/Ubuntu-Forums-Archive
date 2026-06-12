---
title: "nvidia x server setting"
date: 2013-09-28
forum: Multimedia Software
---

### Post by jgw on 2013-09-28
I am wondering if there is a thread, or documentation, on the nvidia x server settings.  I need to know just what the advanced settings mean/do.  For instance, in the resolution settings there are three things.  The first and last seem to be the same.  The middle one has something to do with display port and the setting has WidthXHeightX??x??   I have messed with this one some but would really like to know exactly what these settings do.  For instance, can I go for a smaller amount of resolution and then blow it up on the screen so that I can see it from far away? (like 15/20 feet away).  My screen is a 65" tv.  My resolution, now, is something like 1850x1050  the middle looks like 1050x1050x40x10  I have spent a lot of time trying to get it right buy have no idea what in the world I am doing.

There is also the problem that my screen output is not square, its off about a half an inch width wise and about the same on the bottom.  This is all pretty mysterious to me and I would appreciate it if somebody could point me to the info.  I have search but failed.

Thank you...................

---

### Post by papibe on 2013-09-28
Hi jgw.

One of the most common problems to connect a computer to a TV is [overscan]("http://en.wikipedia.org/wiki/Overscan"). Very annoying and usually it is the TV's fault. 

I'd try to set an standard TV resolution (1920x1080p or 1280x720p) on the computer, and then I'd try to solve its fitting using the TV's remote. 

For example, in the case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

I'm not 100% familiar with the new Nvidia metamodes and viewports, but I understand that now you can set virtual resolutions (software scaling), over the actual hardware resolutions. Then are very fun to play with, but they are very blurry.

Nevertheless, if you can't adjust the resolution using your TV remote, then you're left to solve the problem using the viewports.

Let us know if that helped, and if you need more help with that.
Regards.

---

### Post by jgw on 2013-10-04
Thank you for the reply.  Its all very mysterious.  I would study on it if there was anyplace to study on it but I cannot find it.  I am now posting another about themes as that truly confuses.  I have run through many but I stopped when things just started disappearing.  I am also running with a cursor which is credulously small and really hard to see.  I did manage to change to color to red but then it switched back to white.  the only savior is the ability to press control to see where the cursor is.  

I have also tried to find some kind of magnification mechanism.  I actually think that is lurking around but I can't find that either although I have found references to that.  

I am, incidentally, using a 65 inch samsung tv.  as far as I can tell there is no pixel control there and the nvidia control, as far as I can tell also has no such control.  Then, again, I have no idea what the nvidia control actually do and there is no help (or there is and I simply can't find it.  I have found some help but its general in nature and doesn't exactly give any specifics away)

The overscan thing is interesting.  When I adjust things and save them everything is dandy, right up until I reboot and then moving to an edge always shows me a bit more, not much (after much adjusting) but some.  Then there is the assumption I have a 72" screen, I have no idea where that came from.  I am also passing the hdmi through a receiver so I can control my speakers but it really doesn't care as it is just passing stuff through.  Its very odd and confusing.


Anyway, I continue to fight through this and I appreciate the reply - thanks again!

---

### Post by papibe on 2013-10-05
A few thoughts:

If the settings are not sticking after a reboot try this:
[LIST]
[*]Open the 'Nvidia X Server Settings' as root:
```
gksudo nvidia-settings
```
[*]Set it as you want, and before exiting goto 'X Server Display Configuration' on the left, and on the right press the button that says 'Save to X Configuration File'.
[/LIST]
Sometimes working with a receiver in the middle create a few problems for the computer. It makes it more difficult to read the available resolution and general settings of the display. One common trick to solve this issue is to obtain the EDID information from the monitor, save it in a file, and then hardcode it into the X config file. To do that:
[LIST]
[*]Connect your computer directly to the TV and boot normally.
[*]Once on the desktop open  'Nvidia X Server Settings' and go to 'GPU 0 - (model)' on the left, and press the button 'Acquire EDID' on the right.
[*]Save the file, close the Nvidia window, and double check that the file was saved.
[*]Open your Xorg configuration file:```
gksudo gedit /etc/X11/xorg.conf
```
[*]Look for a section called 'Device' and add a custom EDID option:
```
Section "Device"
        ...
	Option	"CustomEDID"  "DFP-0:/path/to/edid.bin"
        ...
EndSection
```
[*]DFP-0 should work as a reference to your main monitor, but it could be DFP-1 or similar. Use the proper path to the place you saved the EDID file.
[*]Save the file, connect back your receiver as it was, and restart your computer.
[/LIST]
Hope this give you more tools to solve your problem. Let us know how it went.
Regards.

---

### Post by jgw on 2013-10-05
Thank you for the reply.

I will make a run at this as you have revealed secrets!! <G>

Thanks again..............

---

### Post by jgw on 2013-10-05
I did as you suggested, insofar as the edid file thing.  There were options and I saved the information as ascii in a file called edid.txt  I choose ascii as the configuration was in that format.  Then I noticed that you saved a bin file.  I took a look at the txt file and it looked like binary code.  I can go back and change that if you think I should.  Getting the direct hdmi connection was a bugger as the tv kept blanking, showing, blanking, etc. but I finally got that done.  I then took a look at what changed.  My display now has a very slight bow (dipping in middle, heighth and width).

To make the screen fit, with no moving if cursor over the edge the resolution is 1860x1050, the out port is 1860x1050x40x10 (I have no idea what the last two mean but to make everything fit it was necessary to do that.  The device remains my denon passthrough although I also have an option to change that to X 0  (I have, again, what that means so I have left it on the denon.

If I leave it at 1920x1080 it seriously overscans horizontally and vertically.  (I think overscan means that when the cursor goes to an edge the picture moves - in this case, up and down, left and right).  I think my confusion happens because of my understanding of resolution and picture size.  I am, I think, obviously dealing with picture size rather than resolution.  

I continue, however, to read and hopefully learn.  Thank you again for the help.

---

### Post by papibe on 2013-10-08
Try something like this:
```
nvidia-settings --assign CurrentMetaMode="DFP-0: 1920x1080 { ViewPortOut=1860x1050x40x10 }"
```
or this:
```
nvidia-settings --assign CurrentMetaMode="DFP-0: 1920x1080 { ViewPortOut=1860x1050x40x10, ViewPortIn=1920x1080 }"
```
Let us know how it goes.
Regards.

---

