---
title: "4OD, Demand 5"
date: 2013-05-11
forum: Multimedia Software
---

### Post by HollyTrolly on 2013-05-11
Hi All,
I'm new to all of this but my boyfriend installed ubuntu on my laptop and since then I've not been able to watch anything on 4OD or Demand 5.
I've googled it till I'm blue in the face and all sources tell me to download HAL then clear the Flash cache folder.
I've done this, Another guide told me to totally remove flash and then re-install it. I've done that also.

Every time even if I reboot on every step I get the same error messages.

Everything loads, On demand 5 i click the play button in the middle of the screen and straight afterwards a box appears that says

"This player is unable to play protected content at this time."

If I try 4OD, the same happens again

"A digital rights error 3322 has occurred..."

Its a pain in the bum because I watch lots of content on the on demand services and now they just wont play.
When I was on ubuntu 12.10 it seemed to work fine, now I'm on 13.04 it doesn't work at all!

Any help would be very much appriciated 

Many Thanks

Holly

---

### Post by GeetFai on 2013-05-18
I'm in the same boat as you :( well apart from the boyfriend and being a girl ;)
Can anyone help? 4OD ( [www.channel4.com]("http://www.channel4.com")) has always been flakey with my Ubuntu installs. I started with 12.04 and it works one month then doesnt the next. In softwareCentre it says I have HAL installed and I have deleted the .adobe folder numerous times but to no avail. It is Big Bang Theory I am trying to watch and yes I am in UK. Is there another .adobe folder I should be deleting instead of just the one in my home directory?
Oh and before I have had to make sure im signed into 4OD or it wouldnt work but clearing my cookies and cache then signing back in didnt do anything.

Thanks for any input folks.

GeetFai

---

### Post by coldraven on 2013-05-19
4OD is working for me at the moment. All I did was to install hal.
Using Firefox with AdblockPlus it even skips the adverts. This is an improvement because for a while it would play the adverts but not the content :(
Chromium also works, I do not have any add-ons so I see adverts.
I'm running Ubuntu 12.10.

Edit: FWIW In Firefox I also have these add-ons
Ghostery
Flash-aid
RefControl
Better Privacy
NoScript

---

### Post by billio on 2013-06-11
This problem with 4OD and Demand5 on 13.04 also applies to Chrome in my case.

---

### Post by hyattjon on 2013-06-28
Close all browser windows and then:

Remove the adobe cache:

    rm ~/.adobe -rf

Install hal & hal-info:

    sudo apt-get install hal hal-info

Reinstall adobe player:

    sudo apt-get install flashplugin-installer --reinstall

All should be well...

---

### Post by onefthemany on 2013-08-06
> **hyattjon said:**
> Close all browser windows and then:

Remove the adobe cache:

    rm ~/.adobe -rf

Install hal & hal-info:

    sudo apt-get install hal hal-info

Reinstall adobe player:

    sudo apt-get install flashplugin-installer --reinstall

All should be well...

dont work for me

still cant watch 4oD on Firefox, Chromium or Chrome :(

---

### Post by muppet317 on 2013-09-01
> **hyattjon said:**
> Close all browser windows and then:

Remove the adobe cache:

    rm ~/.adobe -rf

Install hal & hal-info:

    sudo apt-get install hal hal-info

Reinstall adobe player:

    sudo apt-get install flashplugin-installer --reinstall

All should be well...

I also tried this and I still get the same error messages using firefox and chromium.

Any other suggestions?

---

### Post by KryoMouse on 2013-09-12
After yesterday's update to Flash this has started happening to me, too. hal packages were already installed, cleared the adobe cache too but got nothing as a result.

---

### Post by a-ciccantelli on 2013-10-09
The problem is that demand 5 and 4od and google play use flash DRM.

You can get these sites working in Ubuntu but it is gettting harder and harder 
e.g. the 'hal' packages have now been deleted from the ubuntu 13.10 repos !

here is what you need to do:

1) make sure you are using firefox or chromium
if you are using chrome make sure the pepper flash plugin is turned off

2) if using ubuntu version[COLOR=#000000][FONT=Arial] 13.10 must download and install these raring(13.04) .debs because they have been deleted from the 13.10 repos:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]libhal1:[/FONT][/COLOR]
[COLOR=#1155CC]_[http://packages.ubuntu.com/raring/libhal1](http://packages.ubuntu.com/raring/libhal1)_[/COLOR]

[COLOR=#000000][FONT=Arial]libhal-storage1:[/FONT][/COLOR]
[COLOR=#1155CC]_[http://packages.ubuntu.com/raring/libhal-storage1](http://packages.ubuntu.com/raring/libhal-storage1)_[/COLOR]

[COLOR=#000000][FONT=Arial]hal:[/FONT][/COLOR]
[COLOR=#1155CC]_[http://packages.ubuntu.com/raring/hal](http://packages.ubuntu.com/raring/hal)_[/COLOR]


3) Once the debs are installed, [COLOR=#000000][FONT=Arial]then patch hal by [/FONT][/COLOR][COLOR=#333333][FONT=Arial]executing the following shell commands:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]:[/FONT][/COLOR]

[COLOR=#2060A0][FONT=Verdana]**sudo**[/FONT][/COLOR][COLOR=#2060A0][FONT=Verdana]**mkdir**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**etc**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**hal**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**fdi**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**preprobe**[/FONT][/COLOR]
[COLOR=#2060A0][FONT=Verdana]**sudo**[/FONT][/COLOR][COLOR=#2060A0][FONT=Verdana]**mkdir**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**etc**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**hal**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**fdi**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**information**[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**usr**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**sbin**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**hald **[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**--daemon**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**=**[/FONT][/COLOR][COLOR=#2060A0][FONT=Verdana]**yes**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**--verbose**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**=**[/FONT][/COLOR][COLOR=#2060A0][FONT=Verdana]**yes**[/FONT][/COLOR]

4) [COLOR=#333333][FONT=Arial]**close the browse**[/FONT][/COLOR][COLOR=#333333][FONT=Arial]r and clear the Adobe Access directories by executing the following shell commands:
[/FONT][/COLOR][COLOR=#333333][FONT=Courier New]cd ~/.adobe/Flash_Player[/FONT][/COLOR]
[COLOR=#333333][FONT=Courier New]rm -rf NativeCache AssetCache APSPrivateData2[/FONT][/COLOR]
[COLOR=#2060A0][FONT=Verdana]rm[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]-rf[/FONT][/COLOR][COLOR=#333333][FONT=Verdana] ~[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]/[/FONT][/COLOR][COLOR=#333333][FONT=Verdana].adobe[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]5) need to reset licence files (this is critical too !):[/FONT][/COLOR]
[COLOR=#1155CC][U][http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager08.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager08.html)

6) [/U][/COLOR][COLOR=#000000][FONT=Arial]test via:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]****[/FONT][/COLOR]
[[COLOR=#DD5424][FONT=Times New Roman]**[http://drmtest2.adobe.com:8080/SVP/SampleVideoPlayer_FP.html](http://drmtest2.adobe.com:8080/SVP/SampleVideoPlayer_FP.html)**[/FONT][/COLOR]]("http://drmtest2.adobe.com:8080/SVP/SampleVideoPlayer_FP.html")
[COLOR=#000000][FONT=Arial]****[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]paste in this video url:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]http://drmtest2.adobe.com:8080/Content/anonymous.f4v[/FONT][/COLOR]

---

### Post by RobMagus on 2013-10-09
I can confirm that following a-ciccantelli's steps works. I was unable to view anything on 4od for months, and now it works perfectly. Thanks!

- r

---

### Post by a-ciccantelli on 2013-10-09
I think more people are using games consoles, smart TVs, roku boxes and tablets to view these services now so it doesn't seem to be a priority to keep this stuff working any more ?

---

### Post by muppet317 on 2013-10-20
Thanks [**[COLOR=#000000]a-ciccantelli[/COLOR]**]("http://ubuntuforums.org/member.php?u=1868969") - problem solved, all seems to be working fine using that method.

---

### Post by muppet317 on 2013-10-20
It solved the DRM problem with 4od - however I'm now experiencing problems with hal  - bug report is here [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/1182801](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/1182801)

At boot up I get this repeated error message: 
> systemd-udevd[992]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory

According to the bug report there is no fix for this problem with hal. 

Anyone know a way of fixing this so you can get hal to work for DRM/flash issues, without these problems?

---

### Post by plansk on 2013-10-21
Oh brilliant muppet317, following your lead from the bug report (since [**[COLOR=#000000]a-ciccantelli[/COLOR]**]("http://ubuntuforums.org/member.php?u=1868969")'s solution of using the Raring 13.04 version didn't work for me for 13.10) I installed Michael Blennnerhassett's "zombie hal" package and now 4od (and guardian flash) work for me (see [https://launchpad.net/~mjblenner/+archive/ppa-hal):](https://launchpad.net/~mjblenner/+archive/ppa-hal):)

sudo add-apt-repository ppa:mjblenner/ppa-hal
sudo apt-get update
sudo apt-get install hal

Thanks to all concerned!

---

### Post by kabub on 2013-10-26
> **plansk said:**
> Oh brilliant muppet317, following your lead from the bug report (since [**[COLOR=#000000]a-ciccantelli[/COLOR]**]("http://ubuntuforums.org/member.php?u=1868969")'s solution of using the Raring 13.04 version didn't work for me for 13.10) I installed Michael Blennnerhassett's "zombie hal" package and now 4od (and guardian flash) work for me (see [https://launchpad.net/~mjblenner/+archive/ppa-hal):](https://launchpad.net/~mjblenner/+archive/ppa-hal):)

sudo add-apt-repository ppa:mjblenner/ppa-hal
sudo apt-get update
sudo apt-get install hal

Thanks to all concerned!

This finally worked for me! Thank you for posting it, I was going nuts with this issue!

---

### Post by muppet317 on 2013-10-27
Thanks plansk - hadn't spotted that - that's now solved all the problems, DRM is working and no start up problems. Thanks!

---

### Post by phil smart on 2013-11-07
Hi there I worked through this set of instructions in Ubuntu13.10( 32 bit)
when I paste in the test video the message comes" loading flash access licence" but never plays the video.
Any help would be great
Phil

---

### Post by j.j.veilleux on 2013-12-14
I confirm that the procedure in a-ciccantelli's post solves the problem. I have just use this procedure to get Amazon Instant Videos working on my laptop running Ubuntu 13.10. I am a very happy camper!

A couple of comments/clarifications:

As also mentioned by others above, in step 2, there are actually two ways to do this:

1. Get the deb's from the 13.04 repository locations mentioned in a-ciccantelli's post, and install them using 'sudo dpkg -i <deb-filenames>'. -- but, this does not totally seem to work; it works as far as fixing the DRM problem and allowing you to watch DRM-protected videos, but causes a problem at startup as mentioned in muppet317 above.

   2. The solution which seems to fix the DRM issue and not cause the problem at startup is to add an alternate repo, where hal is apparently still being maintained, to your list of apt repositories, then install hal more simply by just using apt-get:

  sudo add-apt-repository ppa:mjblenner/ppa-hal
  sudo apt-get update
  sudo apt-get install hal

NOTE: I cannot take credit for this information; I found it in a post by 'noobninja' here: [http://askubuntu.com/questions/362259/how-to-watch-videos-in-amazon-prime-instant-video-after-upgrading-to-ubuntu-13-1](http://askubuntu.com/questions/362259/how-to-watch-videos-in-amazon-prime-instant-video-after-upgrading-to-ubuntu-13-1). (I subsequently also noticed it in the subsequent comments above; doh! That's what I get for reading only the part of the thread that I thought I needed! Next time I'll read the whole thing).

In step 3, the commands shown above are a little bit mangled (missing spaces). The commands should actually be:

sudo mkdir /etc/hal/fdi/preprobe
sudo mkdir /etc/hal/fdi/information
/usr/sbin/hald --daemon=yes --verbose=yes

In step 4, you only have to execute the last command ('rm -rf ~/.adobe'). The two commands above that one are redundant and unnecssary, since they're just deleting lower-level directories that would also be deleted by the last command. So -- just do 'rm -rf ~/.adobe'.

---

### Post by nallison19 on 2013-12-16
Note these debian packages no longer work. They worked for me at this ppa if you trust archived packages of hal you can access them here [https://launchpad.net/~mjblenner/+archive/ppa-hal](https://launchpad.net/~mjblenner/+archive/ppa-hal)
then use apt-get to install libhal1, libhal-storage1, and hall and you will be back to watching amazon instant video on firefox
> **a-ciccantelli said:**
> The problem is that demand 5 and 4od and google play use flash DRM.

You can get these sites working in Ubuntu but it is gettting harder and harder 
e.g. the 'hal' packages have now been deleted from the ubuntu 13.10 repos !

here is what you need to do:

1) make sure you are using firefox or chromium
if you are using chrome make sure the pepper flash plugin is turned off

2) if using ubuntu version[COLOR=#000000][FONT=Arial] 13.10 must download and install these raring(13.04) .debs because they have been deleted from the 13.10 repos:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]libhal1:[/FONT][/COLOR]
[COLOR=#1155CC]_[http://packages.ubuntu.com/raring/libhal1](http://packages.ubuntu.com/raring/libhal1)_[/COLOR]

[COLOR=#000000][FONT=Arial]libhal-storage1:[/FONT][/COLOR]
[COLOR=#1155CC]_[http://packages.ubuntu.com/raring/libhal-storage1](http://packages.ubuntu.com/raring/libhal-storage1)_[/COLOR]

[COLOR=#000000][FONT=Arial]hal:[/FONT][/COLOR]
[COLOR=#1155CC]_[http://packages.ubuntu.com/raring/hal](http://packages.ubuntu.com/raring/hal)_[/COLOR]


3) Once the debs are installed, [COLOR=#000000][FONT=Arial]then patch hal by [/FONT][/COLOR][COLOR=#333333][FONT=Arial]executing the following shell commands:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]:[/FONT][/COLOR]

[COLOR=#2060A0][FONT=Verdana]**sudo**[/FONT][/COLOR][COLOR=#2060A0][FONT=Verdana]**mkdir**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**etc**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**hal**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**fdi**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**preprobe**[/FONT][/COLOR]
[COLOR=#2060A0][FONT=Verdana]**sudo**[/FONT][/COLOR][COLOR=#2060A0][FONT=Verdana]**mkdir**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**etc**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**hal**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**fdi**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**information**[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**usr**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**sbin**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**hald **[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**--daemon**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**=**[/FONT][/COLOR][COLOR=#2060A0][FONT=Verdana]**yes**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**--verbose**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**=**[/FONT][/COLOR][COLOR=#2060A0][FONT=Verdana]**yes**[/FONT][/COLOR]

4) [COLOR=#333333][FONT=Arial]**close the browse**[/FONT][/COLOR][COLOR=#333333][FONT=Arial]r and clear the Adobe Access directories by executing the following shell commands:
[/FONT][/COLOR][COLOR=#333333][FONT=Courier New]cd ~/.adobe/Flash_Player[/FONT][/COLOR]
[COLOR=#333333][FONT=Courier New]rm -rf NativeCache AssetCache APSPrivateData2[/FONT][/COLOR]
[COLOR=#2060A0][FONT=Verdana]rm[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]-rf[/FONT][/COLOR][COLOR=#333333][FONT=Verdana] ~[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]/[/FONT][/COLOR][COLOR=#333333][FONT=Verdana].adobe[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]5) need to reset licence files (this is critical too !):[/FONT][/COLOR]
[COLOR=#1155CC][U][http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager08.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager08.html)

6) [/U][/COLOR][COLOR=#000000][FONT=Arial]test via:[/FONT][/COLOR]
[COLOR=#DD5424]**[http://drmtest2.adobe.com:8080/SVP/SampleVideoPlayer_FP.html](http://drmtest2.adobe.com:8080/SVP/SampleVideoPlayer_FP.html)**[/COLOR]


[COLOR=#000000][FONT=Arial]paste in this video url:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]http://drmtest2.adobe.com:8080/Content/anonymous.f4v[/FONT][/COLOR]

---

### Post by nospam3 on 2013-12-23
Works for me as well.
Great, thanks. :)

---

### Post by ajf.me on 2014-01-04
> **plansk said:**
> Oh brilliant muppet317, following your lead from the bug report (since [**[COLOR=#000000]a-ciccantelli[/COLOR]**]("http://ubuntuforums.org/member.php?u=1868969")'s solution of using the Raring 13.04 version didn't work for me for 13.10) I installed Michael Blennnerhassett's "zombie hal" package and now 4od (and guardian flash) work for me (see [https://launchpad.net/~mjblenner/+archive/ppa-hal):](https://launchpad.net/~mjblenner/+archive/ppa-hal):)

sudo add-apt-repository ppa:mjblenner/ppa-hal
sudo apt-get update
sudo apt-get install hal

Thanks to all concerned!

Thanks a bunch! This fixed it for me, both the device binding and corrupt global state issues :)

---

### Post by king.of.random on 2014-01-07
For information a bug has been raised on launchpad hal :[COLOR=#333333][FONT=Ubuntu]**Bug #1221254 **[/FONT][/COLOR]

---

### Post by king.of.random on 2014-01-10
Actually this worked for me:[http://www.omgubuntu.co.uk/2013/10/fixing-amazon-prime-streaming-drm-protected-flash-13-10Hope](http://www.omgubuntu.co.uk/2013/10/fixing-amazon-prime-streaming-drm-protected-flash-13-10Hope) this helps.

---

### Post by Flash__Gordon on 2014-01-13
To watch DRM protected Flash videos with Linux you need to install pipelight which will allow you to not only enable the updated windows version of Flash plugin in your native linux browser (Firefox or Chrome). But will also allow silverlight to be used for Netflix. 

sudo add-apt-repository ppa:pipelight/stable    (I don't know why or how to turn off stupid smiley face that shows up after ppa should be a colon then pipelight/stable)

sudo apt-get update

sudo apt-get install pipelight-multi

sudo pipelight-plugin --enable silverlight

sudo pipelight-plugin --enable flash

Pipelight should now install the windows version of Flash the first time you start your browser and the plugin gets loaded. The only problem is that you may have several versions of Flash installed and your browser may choose the linux version when opening a Flash application.

To ensure you have only the pipelight Flash enabled see here for instructions.  [http://fds-team.de/cms/pipelight-installation.html#section_2_3](http://fds-team.de/cms/pipelight-installation.html#section_2_3)

 (especially if you already have flash installed for Linux. Could be avoided by completely removing all instance of Flash prior following above instructions.

---

### Post by king.of.random on 2014-01-17
Flash_Gordon thanks for your input on this and I will try this solution as it looks promising. 

As an update I have contacted Channel4 regarding this issue and they seem vaguely interested in providing an app to provide support for 4od as they do for Android. I know it will be probably closed source but could be better than nothing and provide an easy solution in the future of Ubuntu and Linux in general. I guess if more people email them they will realise there is a demand for this on Linux. 

[http://www.channel4.com/4viewers/contact-us](http://www.channel4.com/4viewers/contact-us)

---

### Post by Flash__Gordon on 2014-01-18
> **king.of.random said:**
> Flash_Gordon thanks for your input on this and I will try this solution as it looks promising. 

As an update I have contacted Channel4 regarding this issue and they seem vaguely interested in providing an app to provide support for 4od as they do for Android. I know it will be probably closed source but could be better than nothing and provide an easy solution in the future of Ubuntu and Linux in general. I guess if more people email them they will realise there is a demand for this on Linux. 

[http://www.channel4.com/4viewers/contact-us](http://www.channel4.com/4viewers/contact-us)

Hope it works as well for you as it has for me.

---

### Post by monkeybrain20122 on 2014-01-18
> **Flash__Gordon said:**
> 
To ensure you have only the pipelight Flash enabled see here for instructions.  [http://fds-team.de/cms/pipelight-installation.html#section_2_3](http://fds-team.de/cms/pipelight-installation.html#section_2_3)
.

It is actually a better idea to be able to enable pipelight flash only when needed as my experience shows that when both versions of flash works, pipelight flash is not as smooth and takes longer to load, also some features like webcam, some buttons and some audio don't work with pipelight flash.

The easiest way to switch is to install galternatives from the repo,  open it, go to Mozilla flashplugin and add the path of pipelight flash and then choose which ever you want. This works for Firefox. For Chrome you need to go to about:pplugins and disable/enable which ever flash in question. Anyway piplelight wouldn't work for Chrome/Chromium after April so I won't worry about it.

---

### Post by Flash__Gordon on 2014-01-20
> **monkeybrain20122 said:**
> It is actually a better idea to be able to enable pipelight flash only when needed as my experience shows that when both versions of flash works, pipelight flash is not as smooth and takes longer to load, also some features like webcam, some buttons and some audio don't work with pipelight flash.

The easiest way to switch is to install galternatives from the repo,  open it, go to Mozilla flashplugin and add the path of pipelight flash and then choose which ever you want. This works for Firefox. For Chrome you need to go to about:pplugins and disable/enable which ever flash in question. Anyway piplelight wouldn't work for Chrome/Chromium after April so I won't worry about it.

 I have been using pipelight in Chrome for the last couple of weeks and works great. (with flash or silverlight). Maybe they have fixed it in recent updates. (pipelight-multi)

---

### Post by dir22 on 2014-01-23
I followed these instructions and amazon video worked for me. I was using 12.04 and so 

I used software manager to search for libhal1, libhal-storage1 and hal to install. 

my directories /fdi/preprobe and /fdi information already existed so I left them alone. 

I did not know how to resert licence files so I didn't and it didn't seem to matter. 

Bharath

---

### Post by onefthemany on 2014-01-28
I made a clean install on my laptop and then installed hal... now I can watch 4oD and Demand 5, but only in Firefox... if in doubt clean it out :)

Note: I am on 13.10 not 13.04 and pipelight does not work for me when using Chrome

---

### Post by monkeybrain20122 on 2014-01-28
> **onefthemany said:**
> I made a clean install on my laptop and then installed hal... now I can watch 4oD and Demand 5, but only in Firefox... if in doubt clean it out :)

Note: I am on 13.10 not 13.04 and pipelight does not work for me when using Chrome

Hal doesn't work on pepper flash (Chrome). Pipelight should work on Chrome, but then it won't be for long because google is going to ban all NNAPI plugins and extensions on Chromium/Chrome for Linux after April, so I would just stick to Firefox.

---

### Post by riesengreen on 2014-02-18
Hello and thank you for your post. I followed your directions (minus numbers 5 and 6) and now seem able to rent YouTube and Amazon movies once again. (This is in Firefox, running Ubuntu 13.10.)
Does anyone have any thoughts on why it seems to be more challenging to access this kind of content in 13.10 than it was in previous versions? My hope, of course, would be that Ubuntu would be moving towards greater compatibility with these kinds of sites.
Thanks.

---

### Post by chriswthomas on 2014-04-19
Many thanks for this - worked for me!

---

### Post by GnowledgedGnome on 2014-07-25
> **a-ciccantelli said:**
> The problem is that demand 5 and 4od and google play use flash DRM.

You can get these sites working in Ubuntu but it is gettting harder and harder 
e.g. the 'hal' packages have now been deleted from the ubuntu 13.10 repos !

here is what you need to do:

1) make sure you are using firefox or chromium
if you are using chrome make sure the pepper flash plugin is turned off

2) if using ubuntu version[COLOR=#000000][FONT=Arial] 13.10 must download and install these raring(13.04) .debs because they have been deleted from the 13.10 repos:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]libhal1:[/FONT][/COLOR]
[COLOR=#1155CC]_[http://packages.ubuntu.com/raring/libhal1](http://packages.ubuntu.com/raring/libhal1)_[/COLOR]

[COLOR=#000000][FONT=Arial]libhal-storage1:[/FONT][/COLOR]
[COLOR=#1155CC]_[http://packages.ubuntu.com/raring/libhal-storage1](http://packages.ubuntu.com/raring/libhal-storage1)_[/COLOR]

[COLOR=#000000][FONT=Arial]hal:[/FONT][/COLOR]
[COLOR=#1155CC]_[http://packages.ubuntu.com/raring/hal](http://packages.ubuntu.com/raring/hal)_[/COLOR]


3) Once the debs are installed, [COLOR=#000000][FONT=Arial]then patch hal by [/FONT][/COLOR][COLOR=#333333][FONT=Arial]executing the following shell commands:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]:[/FONT][/COLOR]

[COLOR=#2060A0][FONT=Verdana]**sudo**[/FONT][/COLOR][COLOR=#2060A0][FONT=Verdana]**mkdir**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**etc**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**hal**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**fdi**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**preprobe**[/FONT][/COLOR]
[COLOR=#2060A0][FONT=Verdana]**sudo**[/FONT][/COLOR][COLOR=#2060A0][FONT=Verdana]**mkdir**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**etc**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**hal**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**fdi**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**information**[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**usr**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**sbin**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**/**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**hald **[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**--daemon**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**=**[/FONT][/COLOR][COLOR=#2060A0][FONT=Verdana]**yes**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**--verbose**[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**=**[/FONT][/COLOR][COLOR=#2060A0][FONT=Verdana]**yes**[/FONT][/COLOR]

4) [COLOR=#333333][FONT=Arial]**close the browse**[/FONT][/COLOR][COLOR=#333333][FONT=Arial]r and clear the Adobe Access directories by executing the following shell commands:
[/FONT][/COLOR][COLOR=#333333][FONT=Courier New]cd ~/.adobe/Flash_Player[/FONT][/COLOR]
[COLOR=#333333][FONT=Courier New]rm -rf NativeCache AssetCache APSPrivateData2[/FONT][/COLOR]
[COLOR=#2060A0][FONT=Verdana]rm[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]-rf[/FONT][/COLOR][COLOR=#333333][FONT=Verdana] ~[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]/[/FONT][/COLOR][COLOR=#333333][FONT=Verdana].adobe[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]5) need to reset licence files (this is critical too !):[/FONT][/COLOR]
[COLOR=#1155CC][U][http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager08.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager08.html)

6) [/U][/COLOR][COLOR=#000000][FONT=Arial]test via:[/FONT][/COLOR]
[[COLOR=#DD5424][FONT=Times New Roman][/FONT][/COLOR]]("http://drmtest2.adobe.com:8080/SVP/SampleVideoPlayer_FP.html")[COLOR=#DD5424]**[http://drmtest2.adobe.com:8080/SVP/SampleVideoPlayer_FP.html](http://drmtest2.adobe.com:8080/SVP/SampleVideoPlayer_FP.html)**[/COLOR]


[COLOR=#000000][FONT=Arial]paste in this video url:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]http://drmtest2.adobe.com:8080/Content/anonymous.f4v[/FONT][/COLOR]


I am new to Ubuntu and I do not understand how to download [COLOR=#000000][FONT=Arial]libhal1, [/FONT][/COLOR][COLOR=#000000][FONT=Arial]libhal-storage1, [/FONT][/COLOR][COLOR=#000000][FONT=Arial]hal. Can you pleas give a step by step?[/FONT][/COLOR]

---

### Post by todd-4 on 2015-01-10
> **j.j.veilleux said:**
> I confirm that the procedure in a-ciccantelli's post solves the problem. I have just use this procedure to get Amazon Instant Videos working on my laptop running Ubuntu 13.10. I am a very happy camper!

A couple of comments/clarifications:

As also mentioned by others above, in step 2, there are actually two ways to do this:

1. Get the deb's from the 13.04 repository locations mentioned in a-ciccantelli's post, and install them using 'sudo dpkg -i <deb-filenames>'. -- but, this does not totally seem to work; it works as far as fixing the DRM problem and allowing you to watch DRM-protected videos, but causes a problem at startup as mentioned in muppet317 above.

   2. The solution which seems to fix the DRM issue and not cause the problem at startup is to add an alternate repo, where hal is apparently still being maintained, to your list of apt repositories, then install hal more simply by just using apt-get:

  sudo add-apt-repository ppa:mjblenner/ppa-hal
  sudo apt-get update
  sudo apt-get install hal

NOTE: I cannot take credit for this information; I found it in a post by 'noobninja' here: [http://askubuntu.com/questions/362259/how-to-watch-videos-in-amazon-prime-instant-video-after-upgrading-to-ubuntu-13-1](http://askubuntu.com/questions/362259/how-to-watch-videos-in-amazon-prime-instant-video-after-upgrading-to-ubuntu-13-1). (I subsequently also noticed it in the subsequent comments above; doh! That's what I get for reading only the part of the thread that I thought I needed! Next time I'll read the whole thing).

In step 3, the commands shown above are a little bit mangled (missing spaces). The commands should actually be:

sudo mkdir /etc/hal/fdi/preprobe
sudo mkdir /etc/hal/fdi/information
/usr/sbin/hald --daemon=yes --verbose=yes

In step 4, you only have to execute the last command ('rm -rf ~/.adobe'). The two commands above that one are redundant and unnecssary, since they're just deleting lower-level directories that would also be deleted by the last command. So -- just do 'rm -rf ~/.adobe'.

For reference, I am on a brand-new Ubuntu install, Ubuntu 14.04.1 LTS, and the above suggestion worked perfectly for me.

Prior to fix, problem manifested itself in all three browsers installed - Chromium, Chrome, and Firefox (all up to date as of this minute...)

Problem exhibited as the video would load, appear to be about to start, then stop.  It never actually WOULD start, clock would show 0:00.  In some browsers (I think Chromium, but I did not keep notes) it appeared to be continuing to cycle through attempting to start (see timeline showing 0:00 with "pause" icon evident, as if it were playing, then black screen, then timeline shows up again with same display, then black, then timeline, etc...)

After going through the above instructions I now find that I CAN play Amazon Instant Video, however ONLY in Firefox.  Chromium and Chrome still do not work, still exhibit same error behaviour described above.

Don't care, will use Firefox....

Now, if only they had a nice plugin for MythTV...

---

### Post by UncleMonty on 2015-07-07
I can use 40D fine but not demand5 I'm using Ubuntu 14.04 64 bit. Advice please

---

### Post by stevebrodie on 2015-10-24
> **UncleMonty said:**
> I can use 40D fine but not demand5 I'm using Ubuntu 14.04 64 bit. Advice please

Yes I find exactly the same thing on 14.04 64bit. It's frustrating, and the sort of thing that makes it hard to advocate Ubuntu to users of other OS's :(

---

### Post by ghost123uk on 2016-01-09
> **stevebrodie said:**
> Yes I find exactly the same thing on 14.04 64bit. It's frustrating, and the sort of thing that makes it hard to advocate Ubuntu to users of other OS's :(

Same here  :( 

I have a machine here in the workshop that had Vista on it, I persuaded the owner that Linux was the way forward, but she uses it a lot for catch up TV.
ITV hub does not work (just gives a black screen) 5OD just gives the loading circle, but never loads.
This is getting silly what with all this flash and hal issues now. 
I have tried all the usual things, manually putting the newest version of flash that is available to "us" in place, but still no go.

I can see that his one will have to go back to Windows  :( 

The (LOTS) of other machines I have done recently (for customers) will almost certainly have the same issues, it's just that those customers have likely not tried to use catchup TV (btw, the BBC one, and Youtube do work). What will I tell them when they ring up and ask me to get ITV and 5OD working?

This is becoming a major stumbling block. If I cannot find a reliable fix, I may well have to bow out of doing Linux installs  :(

---

