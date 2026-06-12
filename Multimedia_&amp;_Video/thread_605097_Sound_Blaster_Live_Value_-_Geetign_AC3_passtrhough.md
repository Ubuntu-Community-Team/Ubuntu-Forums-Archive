---
title: "Sound Blaster Live Value - Geetign AC3 passtrhough to work"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by harker on 2007-11-06
Hi,

Ok here's my problem.

I can't get digital passthrough to work on my SB Live Value.

Now I know it can do it as I've installed LinuxMCE once (based on ubuntu feisty) and atleast got Dolby Digital passthrough working.

I know it's based on the Emu10k1 chipset, and understood that these drivers were already included in my ubuntu installation (gutsy gibbon).

But I decided to try downloading it and emu-tools from sourceforge, having trouble compling it though

see: [http://ubuntuforums.org/showthread.php?t=603116&highlight=emu10k1]("http://ubuntuforums.org/showthread.php?t=603116&highlight=emu10k1")
 for all the fun I am having trying to do that succesfully.

Anyway, do people have any suggestions. I am a bit of a newb. 

Basically I am trying to get mythtv or rather mythdvd to do the passthrough thing.

To make sure it wasn't how i'd set up mythtv I decided to trying running xine and also vlc separately and setting them to pass through the digital signal. I get nothing.

Like I said I know that my receiver is set up properly because this was working with my last installation.    

Any help would be really appreciated

I don't want to overload this post with predictions of what extra info people might need, so please let me know if I should qualify this post with anything.

harker

---

### Post by Jabone on 2007-11-27
Hi,

I don't know if it's a bug or something but I've lost AC-3 a lot. 

You could try to rename /etc/init.d/alsa-utils to /etc/init.d/alsa-utils.GONE to get the default settings.

It sometimes helped for me. 

Now I'm having asound.conf file from which I can restore the settings that used to work for AC3. I got that file from a working system with command alsactl store and copied it from /var/lib/alsa/ to my home directory. 

It's quite strange that when you try to use /etc/init.d/alsa-utils restart it rewrites that asound.state file with wrong parameters so when restarted the wrong parameters are loaded and AC3 won't work. 

You can try to boot with livecd and get that file and use it on your own system. 

Hopefully that helps.

---

