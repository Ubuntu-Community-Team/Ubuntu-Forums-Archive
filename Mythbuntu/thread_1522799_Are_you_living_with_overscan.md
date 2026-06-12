---
title: "Are you living with overscan?"
date: 2010-07-02
forum: Mythbuntu
---

### Post by itlarson on 2010-07-02
For two years I have lived with overscan on my 50" 720p plasma tv.  It has HDMI as it's only digital input, and will only accept the standard broadcast resolutions up to 1080p, not it's native 1366x768.  it has nothing in it's settings to compensate for overscan or allow for a 1:1 pixel mapping.  Here is the workaround I  use:

-In mythfronted settings I set the gui size so it isn't off the edge of the screen.  tv playback I watch overscaned, since it looks fine that way- you can't tell the difference.

-In xfce settings, I set up borders at the edge pf the visible screen.  That way I can maximise a window, and it won't be off the edge of the screen.  Then I turn off the panel.

-Instead of using the panel, I now alt-tab to switch apps..  To start apps, I go to the desktop (ctrl-alt-d) and either use the launchers on the desktop, or right click to get the system menu. The only thing I can't access is the system tray widgets, and the only one of them which I might need is the network manager.  fortunatly my mythbox is wired- in, so network setup isn't an issue.

This system actually works pretty well, since the screen is far enough away that I usually have all apps to be maximised, and just alt-tab between them.  But I would like a more permanent solution to overscan.

I have two questions:

first- is anyone else living with overscan?  What workarounds have you come up with?

Second- is there a real solution in sight?  I keep hearing rumors that this might be fixed in the nvidia drivers, but am not sure if this is a reality yet.  Are there any other hacks which might work?

---

### Post by superm1 on 2010-07-03
At least on both of my TV's i've got solutions:

On one of them if I set the label of the input to "PC", it turns into a 1-1 mapping to it's native resolution.

On the other, I do have an option in the TV's menus to set it to "Fit".

I wouldn't be able to put up with overscan myself for a PC usage scenario.

---

### Post by itlarson on 2010-07-03
Unfortunately it says right in the manual that input from a computer is not supported, and that it only takes 480i, 720p, 1080i and 1080p for input.  There are no settings like you describe in it's menus, and 1366x768 does not come up in nvidia-settings.  

The workaround is actually much more livable than you might think-  the xfce window borders keep everything on the visible part of the screen, and I don't miss the taskbar at all.  It just irritates me that this can't be dealt with in the proper way, though.  I am surprised no one else seems to have this problem-  maybe other people were more careful which TV's they bought than I was.

---

### Post by nickrout on 2010-07-03
if you have a recent nvidia card then you can fix overscan with a slider in nvidia-settings

---

### Post by newlinux on 2010-07-03
I have overscan on one my mythfrontends (a TV I bought long before I thought about making it a fulltime frontend). I rarely use the TV as a desktop thought (more often I ssh or vnc into it), and myth easily adjust video playback for the overscan so no problems. 

Since then I've only bought TVs where I knew overscan wouldn't be a problem.

---

### Post by uncle hammy on 2010-07-03
> **nickrout said:**
> if you have a recent nvidia card then you can fix overscan with a slider in nvidia-settings
I'll 2nd that one.  I started using it on my one frontend that has overscan, and you'd never know it.

---

### Post by yonkiman on 2010-07-04
> **uncle hammy said:**
> I'll 2nd that one.  I started using it on my one frontend that has overscan, and you'd never know it.

Thirded.

---

### Post by itlarson on 2010-07-05
I just installed mythbuntu lucid, and discovered the slider.  My only problem is that I switch between 720p for the desktop, and 1080p for playback.  Does anyone know how to set up xorg to allow this and still save the overscan setting?

---

### Post by nickrout on 2010-07-05
> **itlarson said:**
> I just installed mythbuntu lucid, and discovered the slider.  My only problem is that I switch between 720p for the desktop, and 1080p for playback.  Does anyone know how to set up xorg to allow this and still save the overscan setting?

I believe that the settings for overscan are not stored in org.conf, but in the nvidia-settings file in your home directory.

You could write a short script to change the settings there and restart X I suppose.

Or you could use your myth box as an appliance as it is intended and forget the desktop :)

---

### Post by iitywygms on 2010-07-06
Maybe I am out of the ordinary but I like a little overscan.
Some of the shows I watch have the black and white dots and dashes across the top of the video image.  A little overscan makes it so I can't see them.

---

### Post by newlinux on 2010-07-06
A little overscan is good when watching a lot of TV shows, but not so good for desktop usage when the panels are at the edges of the screen.

---

### Post by itlarson on 2010-07-06
Actually my ideal would be to have a non overscan corrected 1080p mode for watching TV, and a corrected 720p mode for everything else.  The desktop mode is needed so I can have a standalone music player, Firefox, and VLC for DVD playback.  From my experiences with .21 and .23, I'm not crazy about myth's music player or browser, and the DVD player seldom worked right.  I will have to revisit this in .23, since some of the pluggins have been re-written, but its likely I will want Firefox at the very least.

---

### Post by JMcFly on 2010-07-06
I thought Nvidia 195 broke the HDMI audio while including the overscan adjustment feature? Has that been corrected?

---

### Post by itlarson on 2010-07-07
It works ok for motherboard hdmi anyway.

---

### Post by Colonelguf on 2010-07-08
> **itlarson said:**
> -In xfce settings, I set up borders at the edge pf the visible screen.  That way I can maximise a window, and it won't be off the edge of the screen.  Then I turn off the panel.
I also have the overscan problem. I can't seem to find the setting to set up borders in xfce. Can someone tell me where to find this setting? thanks

---

### Post by nickrout on 2010-07-08
> **Colonelguf said:**
> I also have the overscan problem. I can't seem to find the setting to set up borders in xfce. Can someone tell me where to find this setting? thanks

Why don't you use the nvidia-settings slider?

---

### Post by itlarson on 2010-07-10
The border settings are in the xfce4 settings manager under "workspaces".  I am noticing that this setup window actually refers to them as "margins" not borders, now that I am looking at it.  Reasons for not using the slider might be if the picture isn't as good, If there is stuff from the blanking interval showing during playback, or if you are switching video modes for playback.   Instead of the slider, I would prefer an xfce modification to allow the panel to be anchored to the bottom margin.  If you could do this and still have autohide, overscan wouldn't even mater.

---

### Post by nickrout on 2010-07-10
one has to ask why panels are needed at all. It's an appliance :)

---

### Post by Colonelguf on 2010-07-12
> **itlarson said:**
> The border settings are in the xfce4 settings manager under "workspaces".  I am noticing that this setup window actually refers to them as "margins" not borders, now that I am looking at it.  Reasons for not using the slider might be if the picture isn't as good, If there is stuff from the blanking interval showing during playback, or if you are switching video modes for playback.   Instead of the slider, I would prefer an xfce modification to allow the panel to be anchored to the bottom margin.  If you could do this and still have autohide, overscan wouldn't even mater.

Yeah, thanks, that's what I needed. I don't want to stop overscanning the video, just the computer desktop. I have a RPTV that is 1080p, I don't want to scale the video.

---

### Post by movieman on 2010-07-13
> **itlarson said:**
> Second- is there a real solution in sight?

Probably only to wait until the current generation of TV designers die off or retire so we can get some sensible people doing their job instead.

I used to know a guy whose job was to get the best possible picture quality for a major TV station. He was not impressed that he'd provide a near-perfect digital HD signal and then the TVs would take it and perform a random amount of scaling which ensured that it trashed the picture quality that they'd worked hard to produce.

In fact I don't know anyone involved in TV production who's ever had anything good to say about overscan. It made some kind of sense with old analog broadcasts to CRTs, but it makes no sense at all when you're providing a digital signal to a device with discrete pixels.

---

