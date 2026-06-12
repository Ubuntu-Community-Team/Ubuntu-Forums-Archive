---
title: "Install issues with Intel Mac Mini"
date: 2007-10-06
forum: Mythbuntu
---

### Post by drven1005 on 2007-10-06
Some issues I've had install Mythbuntu on an Intel Mac Mini.

Video card:  Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
Sound card:  Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller
Remote:  StreamZap 


Initially the resolution is 640x480, which made finding the Forward button impossible until I un-maximized the installer window and alt-drag'd the window around.  

The video driver used by Mythbuntu is the "intel" driver.  Using this driver, I'm able to select a higher resolution now.  I was able to select 1920x580.  When watching a recorded program, the video quality is awful.  The colors seem very saturated and bleeding.  I changed the video driver in xorg.conf from "intel" to "i810".  This brings me back to being stuck at 640x480, but video play back is normal.  

A known problem with the i810 driver is showing a blue screen when playing back HD content.  

To get around this, I had to add:

Option "LinearAlloc" "16384"

to my xorg.conf file. 

The larger issue is with sound however.  I'm unable to adjust sound at all with in myth.  I've tried using PCM and Master and neither will adjust the volume.  Using aslamixer, I don't see a PCM column.  I can adjust the master or "front" column manually and it does adjust the sound.  This wasn't the case with Ubuntu 7.06.

Also, using the StreamZap remote with the default configs was a little awkward to be honest.  I suggest using:

For .lircrc:
[http://mythic.tv/streamzap_lircrc](http://mythic.tv/streamzap_lircrc)

For /etc/lirc/lircd.conf
[http://lirc.sourceforge.net/remotes/streamzap/PC_Remote](http://lirc.sourceforge.net/remotes/streamzap/PC_Remote)

Any advice on the video and especially the sound issues would be greatly appreciated.

Other than the above issues, the overal process with MythBuntu has been great.

---

### Post by tgalati4 on 2007-10-06
If Mythbuntu is based on Dapper, then you will have a problem.  There is a channel assignment problem in Gnome that causes only Channel 0 to be controlled by the sound mixer.  

You can manually control sound using Alsamixer but you must select the proper channel.

What version of the kernel is Myubuntu built?

>uname -a

What version of Gnome Panel?

>gnome-panel --version

Compare that with Ubuntu 7.06 that worked properly.

I see some compiling in your future . . . .

---

### Post by superm1 on 2007-10-06
Mythbuntu is based on gutsy. 

You really shouldn't need any compiling of anything here.


I wanted to start this in a separate thread so i can paste the discussion I had with an Xorg maintainer last night about this.

Oct 06 00:41:51 <superm1>       bryce, you still here?
Oct 06 00:41:58 <bryce> yup
Oct 06 00:42:30 <superm1>       bryce, can you comment to how recent of a i810 driver we have: whether this patch discussed here will be necessary [http://myt](http://myt)htv.org/wiki/index.php/Installing_MythTV_on_an_Intel_Mac_Mini_using_Ubuntu#Viewing_HD_Material
Oct 06 00:44:17 <bryce> superm1: yeah lemme look
Oct 06 00:45:35 <bryce> night St...ScottK
Oct 06 00:45:43 <bryce> superm1: ok here's the skinny
Oct 06 00:46:06 <bryce> superm1: i810 is deprecated.  Upstream in xorg they alias i810 to "intel" starting with version 2.0
Oct 06 00:46:32 <bryce> for Ubuntu, rather than use the alias, we held back i810 to version 1.7.4
Oct 06 00:46:56 <bryce> as far as I know, there is no "newer" version than that, as development on that driver ceased when intel took over
Oct 06 00:47:26 <bryce> however because the driver is aliased on some platforms, there is a risk that when people say "new i810" they could mean "intel"
Oct 06 00:47:31 <superm1>       bryce, oh interesting.
Oct 06 00:48:16 <bryce> the linked-to instructions however do seem appropriate to our i810 (references to 915resolution, date on posts, et al)
Oct 06 00:48:53 <bryce> as a general rule though, starting with Gutsy you should not need to worry about the i810 driver... encourage users of it to switch t
o intel
Oct 06 00:51:55 <superm1>       bryce, well the thing that sparked this was that a user had to switch to i810 on a mac mini
Oct 06 00:51:57 <superm1>       using gutsy
Oct 06 00:52:07 <superm1>       and pointed me at that, so i was a bit confused with regard to taht
Oct 06 00:52:08 <bryce> ahh
Oct 06 00:52:23 <superm1>       they had said they couldn't get higher resolution otherwise
Oct 06 00:52:38 <bryce> that sounds wonky
Oct 06 00:53:02 <superm1>       yeah that's what i thought.
Oct 06 00:53:18 <bryce> well, as long as they know that i810 is not going to be supported and that they're more or less on their own with it...
Oct 06 00:53:43 <bryce> while the intel driver does have its bugs, at least people will be working on it
Oct 06 00:54:41 <superm1>       the guy posted this in our thread for showing what hardware works and doesnt on mythbuntu.  i'll have him form a more complet
e thread and bring this discussion to him.
Oct 06 00:54:43 <superm1>       thanks bryce :)

---

### Post by superm1 on 2007-10-06
So after reading that, the obvious (to me at least) question is why don't things work with the intel driver?  Have you tried to force higher resolutions with it?  Have you looked at logs and such?

---

### Post by drven1005 on 2007-10-07
> **superm1 said:**
> So after reading that, the obvious (to me at least) question is why don't things work with the intel driver?  Have you tried to force higher resolutions with it?  Have you looked at logs and such?

The only thing that doesn't work is video play back when using the intel driver.  While using the intel driver, I'm able to select higher resolutions, the only thing that doesn't work is video play back.  The only way I can describe the way videos look is the colors are bleeding.  This is the case with both standard and high deffenition content. 

Using the i180 driver, I'm stuck at 640x480.  It's possible I can use 915resolution to modify a bios default resolution, but I haven't tried to do that yet.  Using the screen resolution utility, no resolutions are available for me to select.  Video play back is perfectly fine.  If you want to explore why the i810 driver doesn't allow for a higher resolution (note this is only the case when connected with dvi to an hdtv) then I can post logs.

I'm not sure how to take a screen shot, but if you know of a way I'd be happy to show an example.

---

### Post by superm1 on 2007-10-07
> **drven1005 said:**
> The only thing that doesn't work is video play back when using the intel driver.  While using the intel driver, I'm able to select higher resolutions, the only thing that doesn't work is video play back.  The only way I can describe the way videos look is the colors are bleeding.  This is the case with both standard and high deffenition content. 

Using the i180 driver, I'm stuck at 640x480.  It's possible I can use 915resolution to modify a bios default resolution, but I haven't tried to do that yet.  Using the screen resolution utility, no resolutions are available for me to select.  Video play back is perfectly fine.  If you want to explore why the i810 driver doesn't allow for a higher resolution (note this is only the case when connected with dvi to an hdtv) then I can post logs.

I'm not sure how to take a screen shot, but if you know of a way I'd be happy to show an example.

From the description you list here, here is what I recommend:

File a bug with ubuntu against xserver-xorg-video-intel.  Then file a bug with upstream and link it to the ubuntu bug.  This way we're aware of the bug in Ubuntu, and can also watch it upstream.

---

### Post by pug on 2007-10-08
I'm not having any video issues (but I'm also only doing output to a 15" monitor at 1024x768 at the moment).

I am however unable to get the apple remote working.

I can see stuff is happening in /var/log/syslog when I press a button on the remote, but there is no response from mythtv.

Not sure how to follow up on this, please advice.

oh, for info: Using Kubuntu 7.10 beta as base, everything is fully upgraded

---

### Post by superm1 on 2007-10-08
> **pug said:**
> I'm not having any video issues (but I'm also only doing output to a 15" monitor at 1024x768 at the moment).

I am however unable to get the apple remote working.

I can see stuff is happening in /var/log/syslog when I press a button on the remote, but there is no response from mythtv.

Not sure how to follow up on this, please advice.

oh, for info: Using Kubuntu 7.10 beta as base, everything is fully upgraded
Start off by checking 'irw'

Open up a terminal, type irw and start jamming on the buttons.  If things show up in the console, your remote is 'working'  Just need a valid ~/.lircrc.  You should have one already there, but it might nto be sanely generated.  Need to file a bug against mythbuntu-lirc-generator then.

---

### Post by pug on 2007-10-08
running irw gives me:

connect: Connection refused

Guess its a lirc problem, not sure what to add where though.

---

### Post by superm1 on 2007-10-08
> **pug said:**
> running irw gives me:

connect: Connection refused

Guess its a lirc problem, not sure what to add where though.
Mac mini remotes, lets see.  Don't these listen on an event device?  I believe you need to identify that event device and then put it in /etc/lirc/hardware.conf.  Might be wrong though.

---

### Post by drven1005 on 2007-10-09
I'll get a bug reported submitted in the near future.

Any idea on my volume problem though?  Very annoying that I can not adjust volume in myth anymore....

---

### Post by utexaspunk on 2007-10-26
> **drven1005 said:**
> The only thing that doesn't work is video play back when using the intel driver.  While using the intel driver, I'm able to select higher resolutions, the only thing that doesn't work is video play back.  The only way I can describe the way videos look is the colors are bleeding.  This is the case with both standard and high deffenition content. 

Using the i180 driver, I'm stuck at 640x480.  It's possible I can use 915resolution to modify a bios default resolution, but I haven't tried to do that yet.  Using the screen resolution utility, no resolutions are available for me to select.  Video play back is perfectly fine.  If you want to explore why the i810 driver doesn't allow for a higher resolution (note this is only the case when connected with dvi to an hdtv) then I can post logs.

I'm not sure how to take a screen shot, but if you know of a way I'd be happy to show an example.

I'm having the same problems with bleeding colors. It looks like someone turned the saturation way up or something. Have you found the correct settings? If so, what ended up working?

---

### Post by drven1005 on 2007-10-30
There's been an update to the intel driver, which seemed to help the color issues.  But if I enable XV video controls, it does it again basically.  

To get around this, I had to tune the video settings during video playback.  I had to turn everything way down, to around the 30% range for color, contrast and brightness.

With the new driver, I'm able to select a few different resolutions.  However, with my HDTV connected with DVI, only two work:  640x480 and 1920x540

Neither are really ideal, but at 1920x540, everything seems really stretched.  I'll need to play around with some settings to see if I can get it looking any better, but it would be great if I could select 1920x1080

Also sound is working correctly since the alsa update, too.

---

