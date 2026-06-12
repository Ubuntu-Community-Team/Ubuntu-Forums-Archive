---
title: "Flash doesnt work"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by knowledge_is_power on 2007-12-25
Im positive theres been others with this problem, but i cant find any threads, so if theres been a good solution, please link.
Whenever I load flash stuff, it doesnt work.  It loads, but then freezes either the browser or the whole system.  I have newest firefox, flash (i tried the flash both  ffrom repository and from macromedia tarball) and epiphany.  In epiphany it works once, but the second time i watch a video it freezes the browser.

---

### Post by knowledge_is_power on 2007-12-25
ooook...
update. wwent add/remove programs and selected ubuntu restricted
and cpoied libflashplayer.so from the tarball into /usr/lib/epiphany/2.20/plugins
aand now it works... >.<
ive been trying for WEEKS to solve this problem, and i have no idea why it worked THIS time.
:confused::confused::confused:


UPDATE:  after 1 browser session of it working, i restarted firefox, and it does NOT work.  it freezes the browser on a second movie view.
(ie. I can watch one movie on youtube fine with sound etc, but as soon as i hit a link to another video, browser locks up.)

---

### Post by jslmg on 2008-01-10
Similarly,  I can't view flash-based video on most websites. Youtube works fine, but with CNN.com videos, I get a message in the video window saying "Make sure you do have any Flash-blocking plugins."

What are the possible plugins in epiphany that would be causing that? Ad-block, btw, is installed, but not enabled.

---

### Post by braacken on 2008-01-10
The only way I have successfully installed flash in Firefox was done manually...once you learn, its easy.

I have never got the Gnash (free version) to work correctly and tried numerous times.

Before you begin the manual installation process you need to make sure you remove it from your package manager.  Then verify in Firefox that there is no longer any file type relation with .swf; if so, delete it as well.

Then...go to the adobe website...download the tarball.  Extract it.  Then using terminal, navigate to its location and as root run the script.  The script will execute and ask prompt where to install it and you want to install it in the same directory the example gives except the browsers director is mozilla-firefox

---

### Post by jslmg on 2008-01-12
With braacken's manual install method, I was able to get CNN.com video, for example, working partially in Firefox. Two problems, though:

1) no sound...

2) It still doesn't work in Epiphany, which is my default browser. There is a change, though. Before this install, I only got a white background with a notice saying "connection timed out. Please check that you do not have any flash-blocking plugins installed." Now, I get a black background only.

Any further tips or remedies?

---

### Post by wolfen69 on 2008-01-12
here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then just click and install.

---

### Post by jslmg on 2008-01-12
> **wolfen69 said:**
> here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then just click and install.

Are you referring to flashplugin-nonfree from Synaptic?

I removed that, and all other flash/gnash related files, before installing the Adobe Flash plugin found here:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

I'll go ahead and download the fix you're talking about, then let you know what happens.

---

### Post by jslmg on 2008-01-12
> **wolfen69 said:**
> here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then just click and install.

When I started the installer for this plugin, the installer put up a message saying that an older version of this exists in the repos, and advising me to use that older version because it is "better supported." 

So, this version that wolfen recommends is a more recent one that fixes holes in the old one, is that right?

I went ahead with the installation of this newer plugin, and here's the current state of things:

On Firefox, I have full video from CNN.com, BBC website, and youtube, but no sound. The interface on youtube is now normal, though.

On Epiphany, I have video from BBC and youtube, but no sound. On CNN.com, I only get a black video box, and none of the other video thumbnails are loading.

Next...?

---

### Post by gandaran on 2008-01-12
maybe your problem has nothing to do with flash,provably due to your video card, are you running compiz? if so try going  back to gtk.
make sure you uninstalled mozilla-plugin-gnash.

---

### Post by jslmg on 2008-01-12
> **gandaran said:**
> maybe your problem has nothing to do with flash,provably due to your video card, are you running compiz? if so try going  back to gtk.
make sure you uninstalled mozilla-plugin-gnash.

Just tried that, including reboot. No change. All gnashy things were uninstalled a while back. Issue at this point appears to be more under the audio category than video, though I wouldn't completely rule video out. keep in mind that overall system sound is fine--lack of audio is limited to the web browsers.

---

### Post by GlennW on 2008-01-15
> **gandaran said:**
> maybe your problem has nothing to do with flash,provably due to your video card, are you running compiz? if so try going  back to gtk.
make sure you uninstalled mozilla-plugin-gnash.

I've been following this thread with extreme interest since this has been an issue since my Gutsy upgrade. I've done everything in this thread to no avail. I have great playback at CNN, Stage 6, CBC, and BBC sites. But, big **_but_**, streaming video from youtube and the likes, are still choppy. It loads fine, and then suddenly audio and video stop. The video begins and the audio simultaneously loudly "barfs" up the sound from the stopped video! This is just crazy! How can something work so well in Feisty and just crap out like this? 

Anyway, sorry for the rant, gandaran, can you tell me how to check to see if I've uninstalled the mozilla-plugin-gnash? 

I'm still a relative linux noob and actually know just enough to be very dangerous!

I had to go back to XP the other day for some stupid reason and realized anew why I converted. 

Thanks for the advice.

[ATTACH]56559[/ATTACH]

---

### Post by whoscheesemine on 2008-01-15
> **wolfen69 said:**
> here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then just click and install.

I used your fix on my other computer, and it worked perfectly fine. Everything that I wanted to use that needed flash worked perfectly. However, your link is now dead. Can someone help me out on this one? I have other friends with Ubuntu now who are rather steamed at me that they cannot use YouTube.

EDIT:  I searched the root of your URL and found the one i was looking for. If anyone else needs it, its this one: [http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)

Thanks again.

---

### Post by jslmg on 2008-01-16
> **GlennW said:**
> I've been following this thread with extreme interest since this has been an issue since my Gutsy upgrade. I've done everything in this thread to no avail. I have great playback at CNN, Stage 6, CBC, and BBC sites. But, big **_but_**, streaming video from youtube and the likes, are still choppy. It loads fine, and then suddenly audio and video stop. The video begins and the audio simultaneously loudly "barfs" up the sound from the stopped video! This is just crazy! How can something work so well in Feisty and just crap out like this? 

Anyway, sorry for the rant, gandaran, can you tell me how to check to see if I've uninstalled the mozilla-plugin-gnash?

Go to Applications (menu)-->System-->Administration, then open Synaptic Package Manager. Search for "gnash," remove all related files that show up.

The problem here will not be with the video card. I've got fully functioning video in all apps that need it. The only gap I've got is in sound--I've got video on CNN.com and youtube. I need to know how to enable sound in the web Flash plugin. Once I do that, I'm done with this issue.

---

### Post by GlennW on 2008-01-16
Thanks jslmg. I used Synaptic and searched for "gnash" and found that everything was already uninstalled. So, I'm kind of back where I started from. I just watched a youtube video and the sound and video were interrrupted five times in less than three minutes. This needs a fix..

---

### Post by jslmg on 2008-01-17
My audio issue with flash has been solved. If you are having problems with audio in Flash--particularly NO audio--download this lib file:

[http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb](http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb)

Found at Launchpad bugs page.

---

