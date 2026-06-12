---
title: "media plays...but vry buggy and distorted"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by ride1226 on 2007-01-22
ok so i got my windows partition mounted and can access my itunes folder for music and my documents for all my movies...i downloaded all the codec packages throught synaptic and i can play and watch my movies now. however...my music is vry distorted...there is crackling from time to time...and stuff does not sound right at all...voices sound stretched deepend and just distorted...my video plays...but the colors and just quality are horrible. i am using amaroK to play my music...and w.e the standard video viewer is to watch my movies. running ubuntu 6.06 on a dell 4600C thats about 4 yrs old. my soundcard details are ICH5 family integrated soundcard. if any of that helps. basically just need help gettin this straightened out at music and movies are a huge part of my routine and essential to my linux switch. thanks.

---

### Post by mandrakethepenguin on 2007-01-22
OK, so I assume you are using Totem, the default movie player in GNOME.  Personally, I have problems with Totem as well, the video plays too bright and the colors are messed up.  I use a movie player called Kaffeine, and it plays movies/music/DVDs perfectly.  Type this in a terminal (**Applications => Accessories => Terminal**)```
sudo apt-get install kaffeine
```It is now installed in **Applications => Multimedia => Kaffeine**.

Also, some of your multimedia codecs could be broken or old.  Try using Automatix at [http://www.getautomatix.com]("http://www.getautomatix.com/") to install the right codecs.

---

### Post by ride1226 on 2007-01-22
kaffeine solved my video problem thank you...nice little player too...i used automatix2 last night to install all my codecs...so i dont think theyd be old...is there anything in specific i should or shouldnt install...im using amaroK so play...and for more info its coming off of my windows partition that i mounted. thanks again.

---

### Post by vbdanl on 2007-01-22
can you tell me if kaffeine will play music videos through firefox?  i am going into [www.kzsn.com](www.kzsn.com) and trying to watch some music videos, but i get similar problems - sound is jumpy, sounds like a old record that is skipping, and the video is good sometimes, and jumpy at other times. it opens with mplayer.  i would like it to open in the window that shows up on the screen, but it doesn't.  i have loaded the newest codecs also.  i always get an error as in this screenshot...
thanks for your help.

---

### Post by ride1226 on 2007-01-22
my audio is still weird. not just when playing my mp3s but now that i took the time to turn my audio back on to watch a video its weird too. the video however looks good and plays great. the sound coming from it is distorted just the same as when i play an mp3 in amaroK...this is pretty weird. rly killin my woooo im windoze free buzz if u know what i meen. i know theres gotta be a fix to this im just not experienced enough to even know where to start.

---

### Post by mandrakethepenguin on 2007-01-23
Erm, I'm not too sure why this is.  Your audio should sound right, since Linux has support for this audio chipset. The only thing that I can think of to do is go to **System => Prefrences => Volume** or something along the lines of that.  Hit edit when the volume control window pops up and go to prefrences (I'm running Ubuntu 6.10 server w/Fluxbox so I don't know for sure) and make sure "Front" is checked.  Then crank the volume up on the "Front" interface. I use the same chipset as you on my HP a1220n and this solved my problem when I was on Ubuntu Breezy.  I recommend using Kubuntu rather than Ubuntu because I think it is more user friendly and is better configured to play a variety of multimedia types (If you ever decided to switch).

---

### Post by mandrakethepenguin on 2007-01-23
> **vbdanl said:**
> can you tell me if kaffeine will play music videos through firefox?  i am going into [www.kzsn.com]("http://www.kzsn.com") and trying to watch some music videos, but i get similar problems - sound is jumpy, sounds like a old record that is skipping, and the video is good sometimes, and jumpy at other times. it opens with mplayer.  i would like it to open in the window that shows up on the screen, but it doesn't.  i have loaded the newest codecs also.  i always get an error as in this screenshot...
thanks for your help.And the answer to this question is: I don't think you should be using Firefox. It is a fast browser, but has a long way to go before it is ready to play online media.  Use Konqueror, a KDE browser that plays online media via the Kaffeine plugin. Unfortunately, that plugin is incompatible with Firefox.  To install Konqueror and the corresponding plugin, fire up a terminal and type this in: ```
sudo apt-get install konqueror kmplayer-konq-plugins konqueror-nsplugins
```

---

### Post by vbdanl on 2007-01-24
thank you ride1226 for letting me jump into your thread, and thank you mandrakethepenguin for your help.  i installed the konqueror browser as you suggested, but i am probably over my head with this.  i don't know the difference between ubuntu, kubuntu, and whatever other buntu's there are, nor do i know the diff between gnome and kde.  i am a noobie when it comes to linux.  i have been around unix for several years, but only at work, and using xterm windows and command line stuff - usually use ksh. anyway, i don't know if you thought i had kde or if this browser is compatable with ubuntu/gnome, which is what i think i am running.
it loads, so maybe its ok.  when i went to the website to test the music video out, it first said i needed to load a flash plugin, and directed me to adobe website. i downloaded the rpm, and tried to install it.. here is what i got:
Desktop$ sudo rpm -Uvh flash-plugin-9.0.31.0-release.i386.rpm
Password:
error: Failed dependencies:
        /bin/bash is needed by flash-plugin-9.0.31.0-release.i386
        /bin/sh is needed by flash-plugin-9.0.31.0-release.i386
        libX11.so.6 is needed by flash-plugin-9.0.31.0-release.i386
        libXext.so.6 is needed by flash-plugin-9.0.31.0-release.i386
        libXt.so.6 is needed by flash-plugin-9.0.31.0-release.i386
        libc.so.6 is needed by flash-plugin-9.0.31.0-release.i386
        libc.so.6(GCC_3.0) is needed by flash-plugin-9.0.31.0-release.i386
        libc.so.6(GLIBC_2.0) is needed by flash-plugin-9.0.31.0-release.i386
        libc.so.6(GLIBC_2.1) is needed by flash-plugin-9.0.31.0-release.i386
        libc.so.6(GLIBC_2.1.2) is needed by flash-plugin-9.0.31.0-release.i386
        libc.so.6(GLIBC_2.1.3) is needed by flash-plugin-9.0.31.0-release.i386
        libc.so.6(GLIBC_2.2) is needed by flash-plugin-9.0.31.0-release.i386
        libc.so.6(GLIBC_2.3) is needed by flash-plugin-9.0.31.0-release.i386
        libdl.so.2 is needed by flash-plugin-9.0.31.0-release.i386
        libdl.so.2(GLIBC_2.0) is needed by flash-plugin-9.0.31.0-release.i386
        libdl.so.2(GLIBC_2.1) is needed by flash-plugin-9.0.31.0-release.i386
        libfontconfig.so.1 is needed by flash-plugin-9.0.31.0-release.i386
        libfreetype.so.6 is needed by flash-plugin-9.0.31.0-release.i386
        libglib-2.0.so.0 is needed by flash-plugin-9.0.31.0-release.i386
        libgobject-2.0.so.0 is needed by flash-plugin-9.0.31.0-release.i386
        libgtk-x11-2.0.so.0 is needed by flash-plugin-9.0.31.0-release.i386
        libm.so.6 is needed by flash-plugin-9.0.31.0-release.i386
        libm.so.6(GLIBC_2.0) is needed by flash-plugin-9.0.31.0-release.i386
        libpthread.so.0 is needed by flash-plugin-9.0.31.0-release.i386
        libpthread.so.0(GLIBC_2.0) is needed by flash-plugin-9.0.31.0-release.i386
        libpthread.so.0(GLIBC_2.1) is needed by flash-plugin-9.0.31.0-release.i386
        libpthread.so.0(GLIBC_2.2) is needed by flash-plugin-9.0.31.0-release.i386
        libpthread.so.0(GLIBC_2.2.3) is needed by flash-plugin-9.0.31.0-release.i386
        libpthread.so.0(GLIBC_2.3.2) is needed by flash-plugin-9.0.31.0-release.i386

I also noticed the website said the plugin was for: Browser: Firefox, Mozilla, SeaMonkey and did not mention konqueror.  wasn't sure if that is a problem or not.  i am assuming i already installed this plugin on firefox.  so now i am wondering what all i will have to install again for this browser?  i don't have a problem doing it, just don't understand what is going on..
thanks again for your help..

---

### Post by mandrakethepenguin on 2007-01-24
Oh.  Well, since that screenshot revealed that MPlayer was involved, I assumed some other codec than flash was being used (your screenshot reveals that the video is a mms stream).  If flash is all that you need, then [download the tar.gz]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW") file to your home folder, open up a terminal and then type in the following commands:```
mkdir ~/.mozilla/plugins
tar xvfz install_flash_player_9_linux.tar.gz
cp install_flash_player_9_linux/libflashplayer.so ~/.mozilla/plugins
```If an error occurs typing in the first command, ignore it.  Once this is done go to **Applications => Internet => Konqueror**. Then once in Konqueror go to **Settings => Configure Konqueror.  **Scroll down the sidebar to the left until you see **Plugins**. Click that, then click the "Scan for new plugins" button.  Konqueror should automatically add the plugin that you installed. Firefox should also have Flash installed, but it won't handle the types of media depicted in our screenshot (Firefox can't handle them, Konqueror can).

I assume from the lack of multimedia codecs that you have, you haven't tried [Automatix]("http://www.getautomatix.com/") yet. Automatix installs many common customizations that is not included with the standard Ubuntu installation and is a big time saver.

---

### Post by vbdanl on 2007-01-24
I will try your suggestion tonight when I get home.  Actually I did run automatix, and it installed a bunch of stuff.  Seems like there might have been an error on one or two of the 20 or 30 things it installed, but I can't remember what they were.  That is one of my problems, not knowing how to identify things that did not install properly, and then fix them if/when I do.
I am not sure how to tell what I have and don't have installed.  Is there a command or script you can run that will give you:
 a) the hardware info I see under some peoples posts  
 b) software plugins you have installed   
 c) software by category you have installed, such as multimedia, browsers, games, etc ?
thanks again for your help.

Ok. now its tonight and I tried your suggestions MDTP (thats short for ManDrakeThePenguin).
It played a video after doing your suggestions, but would only play one.  Couldn't seem to get it to play a 2nd one.
I had read a post about sudo and gksudo, and it had a example about starting up firefox with each.
I was wondering if somehow if I have my plugins in the wrong place, maybe because of using sudo when I shouldn't have, or maybe I followed some instructions meant for fc6 instead of ubuntu..
anyway, i tried to run gksudo firefox to see what would happen.  it brought up the browser, and i went into kzsn.com to try a music video.
it didn't work.. looked like it was maybe going to, but never did.
when i exited out of the browser, i saw these error messages in the terminal:
** Message: plugin_get_value 1 (1)
** Message: plugin_get_value 2 (2)
totemGMPPlugin ctor [0x8b55c48]
** Message: NP_Initialize
** Message: totem_plugin_new_instance
Failed to open DBUS session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
totemGMPPlugin dtor [0x8b55c48]
** Message: plugin_get_value 1 (1)
** Message: plugin_get_value 2 (2)
** Message: plugin_get_value 1 (1)
** Message: plugin_get_value 2 (2)
totemGMPPlugin ctor [0x8afd388]
Failed to open DBUS session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
totemGMPPlugin dtor [0x8afd388]
** Message: NP_Initialize
** Message: totem_plugin_new_instance

Does any of this make sense?
also, the one time it played, it seemed to have 3 options for player, xine, gstream, or mplayer.  xine seemed to be disabled?  i tried gstream and it did not work.  i then tried mplayer, and it is the one that played the video, but as i said, only one.

---

