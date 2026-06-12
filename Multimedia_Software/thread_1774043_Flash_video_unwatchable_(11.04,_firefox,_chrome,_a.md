---
title: "Flash video unwatchable (11.04, firefox, chrome, all flash video)"
date: 2011-06-02
forum: Multimedia Software
---

### Post by jstnhickey2 on 2011-06-02
I've been experiencing this problem for many months. Nearly any flash video is completely unwatchable and very choppy.  It is usually out of sync and plays by just skipping frames.  
I have 11.04 installed.  I have used opera, firefox, and chrome browsers.
Video plays properly in all media players, I can play up to 1080 without any lag or choppy video.  
I have the flashaid installed and I'm using the beta build as I have a 64bit system and the stable build is only for 32bit.   I have the ATI FGLRX driver installed.  I have an AMD Athlon 64x 2 QL-65 and 4gb of RAM.  Video plays fine in windows. 
Any ideas?

---

### Post by wolfen69 on 2011-06-02
I would just try the flash-aid mozilla plugin.  [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

It will delete what you have and automatically configure flash for you.

---

### Post by lovinglinux on 2011-06-03
Since you are already using Flash-Aid, I would say your problem is most likely to be an issue with the ATI card. 

Also keep in mind that your movie players are capable of using xv output, which is not CPU intensive. Flash can't do that, so it will use a lot more CPU cycles than videos played locally with Totem or other media player. This can be responsible for the performance difference you are experiencing.

You could try to disable Compiz to see if the problem persists, because Flash and Compiz don't play well together.

Another thing that help some users, is to disable Hardware Acceleration in Flash. Visit YouTube, right-click on the video and select "Settings".

---

### Post by jstnhickey2 on 2011-06-04
how an I disable compiz? I have 11.04 is it possible or will I have to go back to the gnome version?

---

### Post by macaholic on 2011-06-04
> **jstnhickey2 said:**
> how an I disable compiz? I have 11.04 is it possible or will I have to go back to the gnome version?
You won't be able to use Unity if you get rid of compiz. You can either log out and login to a Gnome (No effects) or try [Unity 2D]("http://www.webupd8.org/2011/01/unity-2d-qt-now-available-in-ppa-for.html")
I would try the Gnome without effects session to see if that makes flash videos perform better.

---

### Post by AKADAP on 2011-06-05
The latest version of flash-aid requires an extra step that was not present in previous versions of flash-aid (I just added flash-aid today to fix some issues I had with flash videos). Did you click on the flash-aid icon in the upper right corner of the Firefox window and go through the wizard?

---

### Post by jstnhickey2 on 2011-06-06
yes I used the wizard.  It seeems like its the worst when it first starts.  It may have something to do with the CPU like someone mentioned earlier...  Though it is fine in windows still.  
Will try to run gnome without effects tomorrow.

---

### Post by arshavin on 2011-06-06
> **jstnhickey2 said:**
> I've been experiencing this problem for many months. Nearly any flash video is completely unwatchable and very choppy.  It is usually out of sync and plays by just skipping frames.  
I have 11.04 installed.  I have used opera, firefox, and chrome browsers.
Video plays properly in all media players, I can play up to 1080 without any lag or choppy video.  
I have the flashaid installed and I'm using the beta build as I have a 64bit system and the stable build is only for 32bit.   I have the ATI FGLRX driver installed.  I have an AMD Athlon 64x 2 QL-65 and 4gb of RAM.  Video plays fine in windows. 
Any ideas?

I am having the same problem,but the video is not entirely choppy-I mean, I experience more slow frame rates when I move the cursor over flashplayer window,and although flash somehow works for a while,it ultimately crashes,or even freezes the system,so I've to restart.I 've intel G31 chipset,1GB of DDR2 ram.Natty is more problematic than any other version of Ubuntu that i've ever used.Crashes are quite frequent.:confused::confused::confused::confused::(:(

---

### Post by scooby1970 on 2011-06-07
I updated my 11.04 today and since the update (last updated about a week ago) Youtube video is really slow and choppy. It was perfectly fine before this!  Can anyone help us fix it? I've tried all the above mentioned. Using a Gforce 5700 graphics card that as I said was running Youtube fine before this latest flash update.  :) Mark

---

### Post by s031jd on 2011-07-14
If you can at least run Flash video then you may want to try: 

1. open [http://www.youtube.com](http://www.youtube.com)
2. select a video to run
3. right click on video and select 'Settings'
4. first tab is Display, uncheck 'Enable Hardware Acceleration'
5. close 'Setting' then rerun to test video.

---

### Post by morricone on 2011-07-14
I can confirm this problem. I'm using the fglrx driver. The problem appeared after the updates (See attachment).

---

### Post by lovinglinux on 2011-07-14
If you are using Flash-Aid, execute the Wizard again. Adobe released Flash 11 Beta yesterday, so it might fix your problem, since it fixes recent YouTube issues. You don't need to disable hardware acceleration any more.

---

### Post by appalbarry on 2011-08-02
**3. right click on video and select 'Settings'**

That works in Firefox, but in Chrome the Setting box appears but is dead - can't check the box, tabs can't react. can't cancel out or close Settings.

Chrome 12.0.742.124
Ubuntu 11.4 Natty 2.6.38-10-generic

---

### Post by EkuquoL on 2011-08-02
The Gnash flash plugin is broken... Or somethin.
Uninstall it and use the flashplugin installer

Or you could download the flash pluggin from adobe... Then manually insert it into the plugin folder in the firefox library folder
or the usr/lib/browser-plugin folder. I've had clipping images in flash ... I will possibly be looking into it as I ensure stability of this Ubuntu Server I'm using.

Firefox 5.0 has a embeded nswrapper it should automatically spot the flash plugin.

Also .. you have to be root to move files.

---

