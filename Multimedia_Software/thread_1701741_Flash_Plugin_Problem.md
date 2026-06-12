---
title: "Flash Plugin Problem"
date: 2011-03-06
forum: Multimedia Software
---

### Post by amir786_z on 2011-03-06
hi there guys.. i have a problem that. whenever i am watching videos on youtube, after sometime this error appears "Your flash plugin has encountered an error", and the flash video image stays in the background.. and can b seen through black background and even through letters on every page. and black background of flash videos also gets crappy. dont know what the problem is.. :(:(..

---

### Post by JBAlaska on 2011-03-06
What version of Ubuntu are you using and is it x86 or x86_64. If you are using x86_64 Ubuntu are you using the latest 64bit flash from a PPA.
Have you tried disabling "use hardware acceleration" in flash options.
What browser are you using?
What video card are you using, and what drivers?

---

### Post by inobe on 2011-03-06
after following jb's advice, have a look at flash aid.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by amir786_z on 2011-03-07
> **JBAlaska said:**
> What version of Ubuntu are you using and is it x86 or x86_64. If you are using x86_64 Ubuntu are you using the latest 64bit flash from a PPA.
Have you tried disabling "use hardware acceleration" in flash options.
What browser are you using?
What video card are you using, and what drivers?

1. I am using 32-bit version of ubuntu
2. I dont know how to disable "Use hardware acceleration" in flash
3. I am using Mozilla Firefox
4. My graphic card is Nvidia 9200M GS, driver version is 3.3.0 Nvidia 260.19.06

---

### Post by inobe on 2011-03-07
> **amir786_z said:**
> 1. I am using 32-bit version of ubuntu
2. I dont know how to disable "Use hardware acceleration" in flash
3. I am using Mozilla Firefox
4. My graphic card is Nvidia 9200M GS, driver version is 3.3.0 Nvidia 260.19.06

sporting that great hardware, i am guessing it's a flash issue, and to give flash aid a go.

---

### Post by amir786_z on 2011-03-07
> **inobe said:**
> sporting that great hardware, i am guessing it's a flash issue, and to give flash aid a go.

thank u sir. i have installed the addon flash-aid.. hope this resolves the issue:):)

---

### Post by runeh76 on 2011-03-07
"and the flash video image stays in the background.. and can b seen through black background and even through letters on every page."

I had only that problem, but not error msg. One site was causing it. Dont know why though...
I enabled desktop effects and it was gone.
This was really strange and im wondering it still :confused:

---

### Post by amir786_z on 2011-03-07
and the flash video image can also b seen through desktop wallpaper.. and the desktop wallpapers looks awful :( coz of that flash image stuck in the background.

---

### Post by runeh76 on 2011-03-07
Yeah i had same thing! Can u take picture with digi-camera, so peoples can realize this? I dont own camera and screen-capture doesnt save it.

---

### Post by amir786_z on 2011-03-07
ok i will take a picture this time..

if u r using mozilla then get this addon

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) :)

hope this solves the issue.

---

### Post by runeh76 on 2011-03-07
Chromium here. And i got it solved month ago. Thx and good that u take that pic!

---

### Post by amir786_z on 2011-03-07
ok thats good.. but my chrome does not play any flash videos.. an error appears whenever i play video on chrome "The following plugin has crashed: Shockwave Flash.. 
dont know wat the problem is :(:(:confused:.

---

### Post by runeh76 on 2011-03-07
This is copy from this thread [http://ubuntuforums.org/showthread.php?t=1556090]("http://ubuntuforums.org/showthread.php?t=1556090")


*Type in chrome://plugins in the the Google Chrome address bar.

*Now you will see a list of plugins, click disable on the Shockwave Flash plugin. 

NOW please note,

When I then went to view Youtube (using flash) it said missing plug-in and when I went to download it from Adobe it said something about how my browser already has the latest Flash.

As this was a new version of Ubuntu I had not even yet installed the "restricted extras package" found in Ubuntu software center simply by typing restric... then it shows. After I did that I went to Youtube and it played.

Interestingly while writing this post I noticed I now have TWO Shockwave Flash plugins which are exactly the same, the ONLY difference is one is disabled (obviously) but the location path is /opt/google/chrome/libgcflashplayer.so and the one that works which IS and should be enabled is /usr/lib/flashplugin-installer/libflashplayer.so

This has FIXED the problem, seems Chrome doesn't like running that plug-in from that location.

Thanks LewisDre4m

---

### Post by amir786_z on 2011-03-07
> **runeh76 said:**
> This is copy from this thread [http://ubuntuforums.org/showthread.php?t=1556090](http://ubuntuforums.org/showthread.php?t=1556090)


*Type in chrome://plugins in the the Google Chrome address bar.

*Now you will see a list of plugins, click disable on the Shockwave Flash plugin. 

NOW please note,

When I then went to view Youtube (using flash) it said missing plug-in and when I went to download it from Adobe it said something about how my browser already has the latest Flash.

As this was a new version of Ubuntu I had not even yet installed the "restricted extras package" found in Ubuntu software center simply by typing restric... then it shows. After I did that I went to Youtube and it played.

Interestingly while writing this post I noticed I now have TWO Shockwave Flash plugins which are exactly the same, the ONLY difference is one is disabled (obviously) but the location path is /opt/google/chrome/libgcflashplayer.so and the one that works which IS and should be enabled is /usr/lib/flashplugin-installer/libflashplayer.so

This has FIXED the problem, seems Chrome doesn't like running that plug-in from that location.

Thanks LewisDre4m

1. I found the shockwave plugin and disabled it
2. I have installed "restricted extras package" but still the same error 
3. i have got 2 flash plugins too
    i) [COLOR=#000000][FONT=Times New Roman][FONT=Arial]/usr/lib/adobe-flashplugin/libflashplayer.so
     ii) [/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=Arial]/usr/lib/mozilla/plugins/libflashplayer.so

Still getting same problem..:(
[/FONT][/FONT][/COLOR]

---

### Post by runeh76 on 2011-03-07
pls post that picture.
And log out from Ubuntu and back in.

---

### Post by amir786_z on 2011-03-07
i will post that picture when that flash problem will occur. It occurs in Mozilla not in chrome. Now flash is running normally in Mozilla.:).

Now problem only remains with chrome. it does not play flash videos at all..:(

---

### Post by runeh76 on 2011-03-07
Install Chromium.

---

### Post by amir786_z on 2011-03-07
> **runeh76 said:**
> Install Chromium.

chrome = chromium :).

---

### Post by runeh76 on 2011-03-07
No its not  ;)

---

### Post by amir786_z on 2011-03-07
> **runeh76 said:**
> No its not  ;)

i meant to say that by chrome i mean chromium ;)

---

### Post by runeh76 on 2011-03-07
There are some key differences between Google Chrome and Chromium. First off, Google Chrome is a commercial closed source product made by Google which is based on the open source Chromium project.

Chrome is not available in the default Ubuntu repositories as it's not open source, however Google makes Chrome available through their own 3rd party repository. Chrome is updated by Google directly, as they run the entire repository and update Chrome on their schedule. Since it doesn't need to be redistributable and open source, Chrome includes things that we can't ship in Ubuntu out of the box, like **Flash** and H264 support (See the Ubuntu promise). However you can install this support with a few packages (see below).

Chromium, being open source, is available in the Ubuntu repositories. This is maintained by Ubuntu developers and goes through our Stable Release Update process. Chromium has a release process exception, which allows the team to upload a Chromium build as soon as a new upstream release is made.


Really it depends on what you want. If you trust Google to not break your computer and like the convenience of Chrome then you can use that; if you want an open source browser that is the basis of Chrome that is peer reviewed by Ubuntu developers and doesn't require 3rd party sources then you want Chromium.

[http://askubuntu.com/questions/6253/whats-the-difference-between-google-chrome-and-or-chromium-what-are-the-advanta]("http://askubuntu.com/questions/6253/whats-the-difference-between-google-chrome-and-or-chromium-what-are-the-advanta")

---

### Post by amir786_z on 2011-03-07
> **runeh76 said:**
> There are some key differences between Google Chrome and Chromium. First off, Google Chrome is a commercial closed source product made by Google which is based on the open source Chromium project.

Chrome is not available in the default Ubuntu repositories as it's not open source, however Google makes Chrome available through their own 3rd party repository. Chrome is updated by Google directly, as they run the entire repository and update Chrome on their schedule. Since it doesn't need to be redistributable and open source, Chrome includes things that we can't ship in Ubuntu out of the box, like **Flash** and H264 support (See the Ubuntu promise). However you can install this support with a few packages (see below).

Chromium, being open source, is available in the Ubuntu repositories. This is maintained by Ubuntu developers and goes through our Stable Release Update process. Chromium has a release process exception, which allows the team to upload a Chromium build as soon as a new upstream release is made.


Really it depends on what you want. If you trust Google to not break your computer and like the convenience of Chrome then you can use that; if you want an open source browser that is the basis of Chrome that is peer reviewed by Ubuntu developers and doesn't require 3rd party sources then you want Chromium.

[http://askubuntu.com/questions/6253/whats-the-difference-between-google-chrome-and-or-chromium-what-are-the-advanta](http://askubuntu.com/questions/6253/whats-the-difference-between-google-chrome-and-or-chromium-what-are-the-advanta)

thanks for the info.. i really appreciate it :).

---

### Post by markthekdeguy on 2011-03-07
theres a Firefox plugin called FlashVideoReplacer
which aims to play flash in a proper media player. seems ok, 
if a little flaky on my system. nice.

---

### Post by buckyb on 2011-03-07
> **runeh76 said:**
> There are some key differences between Google Chrome and Chromium. First off, Google Chrome is a commercial closed source product made by Google which is based on the open source Chromium project.

Chrome is not available in the default Ubuntu repositories as it's not open source, however Google makes Chrome available through their own 3rd party repository. Chrome is updated by Google directly, as they run the entire repository and update Chrome on their schedule. Since it doesn't need to be redistributable and open source, Chrome includes things that we can't ship in Ubuntu out of the box, like **Flash** and H264 support (See the Ubuntu promise). However you can install this support with a few packages (see below).

Chromium, being open source, is available in the Ubuntu repositories. This is maintained by Ubuntu developers and goes through our Stable Release Update process. Chromium has a release process exception, which allows the team to upload a Chromium build as soon as a new upstream release is made.


Really it depends on what you want. If you trust Google to not break your computer and like the convenience of Chrome then you can use that; if you want an open source browser that is the basis of Chrome that is peer reviewed by Ubuntu developers and doesn't require 3rd party sources then you want Chromium.

[http://askubuntu.com/questions/6253/whats-the-difference-between-google-chrome-and-or-chromium-what-are-the-advanta]("http://askubuntu.com/questions/6253/whats-the-difference-between-google-chrome-and-or-chromium-what-are-the-advanta")

hmm... I'm detecting a not so subtle bias. Thanks for telling me what to think!

---

### Post by beew on 2011-03-07
> **markthekdeguy said:**
> theres a Firefox plugin called FlashVideoReplacer
which aims to play flash in a proper media player. seems ok, 
if a little flaky on my system. nice.

+1 to that. It actually works flawlessly in all my computers except one which has a vdpau capable nvidia card, somehow when using with flashvideoreplacer in FF4 beta vdpau is not enabled, but works fine in FF3.x  It is a new machine so flash works fine especially now the latest flash uses vdpau. But on my older systems I can barely watch 480p  on Youtube with flash but with the flashvideoreplacer I can watch 720p in full screen.

Another option is minitube. But one has to get version  1.4 from a PPA as the one in Ubuntu's repo is old and broken.

---

### Post by amir786_z on 2011-03-08
thanks all of u guys for the info.. iam trying flash-aid firefox plugin, nothing went wrong by now, if that error occurs again i will give FlashVideoReplacer a shot :).

I dont know wats wrong with my chromium, it does not play any flash videos at all.. an error  appears whenever i play video on chromium "The following plug-in has  crashed: Shockwave Flash".:(

---

### Post by amir786_z on 2011-03-08
Now i got a new problem.. while playing one flash video i play other flash video or i refresh the page my ubuntu hangs:( and i hav to restart my system. i think it coz of flash-aid or maybe it coz of "ubuntu restricted extras":(:sad::sad:

---

### Post by amir786_z on 2011-03-08
> **amir786_z said:**
> Now i got a new problem.. while playing one flash video i play other flash video or i refresh the page my ubuntu hangs:( and i hav to restart my system. i think it coz of flash-aid or maybe it coz of "ubuntu restricted extras":(:sad::sad:

no one knows about this problem?:(

---

### Post by inobe on 2011-03-08
> **amir786_z said:**
> no one knows about this problem?:(

check your system log viewer, see what errors your getting when it freezes, each error will get time stamped, pay mind to the time it freezes and put two and two together.

---

### Post by amir786_z on 2011-03-08
thanks ...
ok i will post the log results when my system freezes again

---

### Post by amir786_z on 2011-03-08
i hav uninstalled "flash-aid" and "Ubuntu Restricted Extras". now the system does not freeze while playing video, when i refresh or see another video :)

---

### Post by inobe on 2011-03-08
> **amir786_z said:**
> thanks ...
ok i will post the log results when my system freezes again

please only post relevant information, if any.

---

### Post by upasakalee on 2011-03-10
> **inobe said:**
> sporting that great hardware, i am guessing it's a flash issue, and to give flash aid a go.

This problem had been bugging me for a while, too.  It looks like Flash-Aid worked.  Thanks a lot. :D

---

### Post by amir786_z on 2011-04-03
Thank GOD problem is solved.. i think mozilla is corrupt or bugged in ubuntu. it causes sound problem and as well as flash problem. so i quit using mozilla and started using chrome. now the things are going well.

thanks guys who helped me.. i appreciate ur help :)

---

### Post by mnordal on 2012-04-18
> **runeh76 said:**
> This is copy from this thread [http://ubuntuforums.org/showthread.php?t=1556090]("http://ubuntuforums.org/showthread.php?t=1556090")


*Type in chrome://plugins in the the Google Chrome address bar.

*Now you will see a list of plugins, click disable on the Shockwave Flash plugin. 

NOW please note,

When I then went to view Youtube (using flash) it said missing plug-in and when I went to download it from Adobe it said something about how my browser already has the latest Flash.

As this was a new version of Ubuntu I had not even yet installed the "restricted extras package" found in Ubuntu software center simply by typing restric... then it shows. After I did that I went to Youtube and it played.

Interestingly while writing this post I noticed I now have TWO Shockwave Flash plugins which are exactly the same, the ONLY difference is one is disabled (obviously) but the location path is /opt/google/chrome/libgcflashplayer.so and the one that works which IS and should be enabled is /usr/lib/flashplugin-installer/libflashplayer.so

This has FIXED the problem, seems Chrome doesn't like running that plug-in from that location.

Thanks LewisDre4m

I had struggled with this for a while and also read other places that the one to be disabled was the "/opt/google/chrome/libgcflashplayer.so" one. However in my case I have to disable "/usr/lib/adobe-flashplugin/libflashplayer.so
" and leave the "/opt/google/chrome/libgcflashplayer.so" enabled.

Running on 10.10 and Chrome v. 18.0.1025.162 (tried 19.x also, same thing)

Just in case someone has same problems as me..

---

