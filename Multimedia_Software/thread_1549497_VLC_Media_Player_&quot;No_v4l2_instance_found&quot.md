---
title: "VLC Media Player &quot;No v4l2 instance found&quot;"
date: 2010-08-09
forum: Multimedia Software
---

### Post by coljohnhannibalsmith on 2010-08-09
Hello,

While using VLC Media Player, I decided to view the "extended settings," to see what adjustments were possible and when I clicked on the "v4l2 controls" tab, the tab displayed the following message:

"No v4l2 instance found.  Press the refresh button to try again."

I pressed the suggested button and nothing changed.  I then installed every entry dealing with "Video for Linux" in Synaptic, rebooted and tried again.  Still no change.

I then Googled to try to find a source tarball, but durring this process I read several posts that suggested that v4l2 is already part or Linux kernels 2.6+.

Is this true?  If so, why does VLC report that there is no v4l2 instance found.  If not, what do I have to do to get v4l2 installed?


Thanks, Hannibal

---

### Post by flick on 2010-08-09
v4l2 is the new generation of video/webcam driver stuff. One interesting possibility to check out its stuff might be :

v4l2ucp

Description: Video for Linux 2 Universal Control Panel
 V4L2UCP is an universal control panel for V4L and V4L2 devices. It reads
 the description of the controls that the device supports from the device
 device, and presents the user with a graphical means for adjusting those
 controls; it allows for controlling multiple devices.

---

### Post by coljohnhannibalsmith on 2010-08-11
Thank you for your reply,

I have already installed that, no change.


Thanks, Hannibal

---

### Post by luigi_mb on 2010-08-11
Did you install "libpt-1.10.10-plugins-v4l2" and "libpt-1.11.2-plugins-v4l2"?

/luigi

---

### Post by coljohnhannibalsmith on 2010-08-12
Good morning Luigi,

Thanks for your reply.  I have those installed as well, no change.



Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2010-08-12
Providing additional information:

When launching "gnome-control-center" from "Terminal" and then launching:
"Video4Linux Control Panel," I receive the following error message:

"Unable to open file /dev/video0
 No such file or directory"

I also get the following error messages in Terminal when launching
"gnome-control-center:"

sophie@sophie-laptop:~$ gnome-control-center

** (gnome-control-center:22751): WARNING **: 
error raised: [libslab_get_gconf_value: error getting /desktop/gnome/applications/main-menu/lock-down/user_modifiable_apps]


** (gnome-control-center:22751): WARNING **: 
error raised: [load_xbel_store: couldn't load bookmark file [NULL]
]


** (gnome-control-center:22751): WARNING **: get_actions_list() - PROBLEM - Can't load gtk-theme-selector.desktop


** (gnome-control-center:22751): WARNING **: get_actions_list() - PROBLEM - Can't load gnome-cups-manager.desktop



Does anyone know what this means or what I should do about it?




Thanks, Hannibal

---

### Post by clockworkpc on 2010-11-07
I get the same problem.

When I try to launch v4l2ucp I get this error message:

Unable to open file /dev/video0
No such device

---

### Post by coljohnhannibalsmith on 2011-04-17
Hello,

After upgrading to Maverick from Lucid, most of those problems went away; however the V4L2 configuration tab in VLC media player was still greyed-out.

I suspect, it may be possible that VLC Media Player looks for the V4L2 instance in a different location.

Here's my thought:

Create a dynamic-link in the folder that VLC Media Player checks, to its actual location; or create a dummy package that does the same thing.

Anyone have any thoughts on how this could be done?



Thanks, Hannibal

---

### Post by no2498 on 2011-04-17
? do you have a webcam plugged in

---

### Post by coljohnhannibalsmith on 2011-05-02
> **no2498 said:**
> ? do you have a webcam plugged in

You must be referring to:

When I try to launch v4l2ucp I get this error message:

Unable to open file /dev/video0
No such device

You nailed me on this one.  I finally figured it out prior to your post; however VLC still doesn't make the configuration settings active with a webcam plugged in.  I tried this in Maverick; but I haven't tested in in Natty yet...

---

### Post by no2498 on 2011-05-03
open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find the cam

keep this in mind as if you use your cam in vlc the cam stops working in all other programs

this gets it back working

---

