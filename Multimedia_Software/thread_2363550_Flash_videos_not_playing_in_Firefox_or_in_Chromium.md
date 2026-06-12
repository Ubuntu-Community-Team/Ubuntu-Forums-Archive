---
title: "Flash videos not playing in Firefox or in Chromium browser in ubuntu 16.04"
date: 2017-06-11
forum: Multimedia Software
---

### Post by AnupamMitra on 2017-06-11
I'm unable to see flash videos, viz. Hotstar in Firefox and/or Chromium browser. My O/S is Ubuntu 16.04  (32 bit). How to fix it?

---

### Post by deadflowr on 2017-06-11
> **AnupamMitra said:**
> I'm unable to see flash videos, viz. Hotstar in Firefox and/or Chromium browser. My O/S is Ubuntu 16.04  (32 bit). How to fix it?

Flash on linux no longer supports DRM-flash.
(Someday, maybe it'll make it back, but currently they had to remove that support in order to update flash for linux)

Alternatives would be to try and run something like Windows Firefox in wine.
Or any browser in a Windows virtual machine.

---

### Post by monkeybrain20122 on 2017-06-11
> **deadflowr said:**
> Flash on linux no longer supports DRM-flash.
(Someday, maybe it'll make it back, but currently they had to remove that support in order to update flash for linux)

Alternatives would be to try and run something like Windows Firefox in wine.
Or any browser in a Windows virtual machine.

Or, if you don't mind doing the work, the freshplayer plugin would work in Firefox provided you extract flash from a Chrome book image rather than using pepper flash bundled with Linux's Chrome.  I have done this way back but I have forgotten the detailed steps, some trial and errors may be required. Using Windows Firefox would work, but this is not elegant. Too bad pipelight has discontinued [https://github.com/i-rinat/freshplayerplugin/blob/master/doc/known-issues.md](https://github.com/i-rinat/freshplayerplugin/blob/master/doc/known-issues.md)

---

### Post by AnupamMitra on 2017-06-13
> **deadflowr said:**
> Flash on linux no longer supports DRM-flash.
(Someday, maybe it'll make it back, but currently they had to remove that support in order to update flash for linux)

Alternatives would be to try and run something like Windows Firefox in wine.
Or any browser in a Windows virtual machine.

Thanks, as advised I installed Windows Firefox in wine.

---

### Post by AnupamMitra on 2017-06-13
> **monkeybrain20122 said:**
> Or, if you don't mind doing the work, the freshplayer plugin would work in Firefox provided you extract flash from a Chrome book image rather than using pepper flash bundled with Linux's Chrome.  I have done this way back but I have forgotten the detailed steps, some trial and errors may be required. Using Windows Firefox would work, but this is not elegant. Too bad pipelight has discontinued [https://github.com/i-rinat/freshplayerplugin/blob/master/doc/known-issues.md](https://github.com/i-rinat/freshplayerplugin/blob/master/doc/known-issues.md)

Thanks **monkeybrain20122**, I have gone through the github link. It is very interesting. I will try it later.

---

### Post by monkeybrain20122 on 2017-06-22
> **monkeybrain20122 said:**
> Or, if you don't mind doing the work, the freshplayer plugin would work in Firefox provided you extract flash from a Chrome book image rather than using pepper flash bundled with Linux's Chrome.  I have done this way back but I have forgotten the detailed steps, some trial and errors may be required. Using Windows Firefox would work, but this is not elegant. Too bad pipelight has discontinued [https://github.com/i-rinat/freshplayerplugin/blob/master/doc/known-issues.md](https://github.com/i-rinat/freshplayerplugin/blob/master/doc/known-issues.md)


I just did it. :)

 After running the scripts linux_recovery.sh,--which needs to be made executable,-- check for the folder tmp.chmosre or something like that in /tmp (forgot to write down the exact name) The chromebook recovery image is the .bin file, copy it somewhere in $HOME.  To mount the image and extract flash, need to install kpartx from the repo, see [https://stackoverflow.com/questions/30732428/extract-files-from-chrome-os-chromebook-recovery-image](https://stackoverflow.com/questions/30732428/extract-files-from-chrome-os-chromebook-recovery-image)

Tested with the adobe DRM test, perfect playback. 
[link]("http://drmtest2.adobe.com:8080/SVP/SampleVideoPlayer_FP.html#") to test page.

video for test [http://drmtest2.adobe.com:8080/Content/anonymous.f4v](http://drmtest2.adobe.com:8080/Content/anonymous.f4v)

For some reason  cut and paste doesn't work on the test page. so need to type in the test video's url manually.

The flash version is just a little behind (45 instead of 46) but it should work fine. One needs to update flash from an up to date chromebook recovery image from time to time. 

It is actually quite simple. If anyone needs help I can post detailed instructions.

---

### Post by 77oma on 2017-07-13
Hello, I was dealing with this issue for a long time, I would really appreciate if you can make a detailed guide (please!)
Thanks in advance.

---

### Post by monkeybrain20122 on 2017-07-14
> **77oma said:**
> Hello, I was dealing with this issue for a long time, I would really appreciate if you can make a detailed guide (please!)
Thanks in advance.

Hi, here is the step by step.

install freshplayerplugin from the webupd8 ppa

```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt update
sudo apt install freshplayerplugin
```


Restart firefox, check your flash version by going to Tools > Addons > Plugins, it should be 26

install kpartx, it will be needed to mount the chromeos image later

```
sudo apt install kpartx
```

To get flash from a ChromeOS recovery image. Download this [script]("https://dl.google.com/dl/edgedl/chromeos/recovery/linux_recovery.sh"). Make it executable (right click, Properties > Permissions check allow execute as program) run it as normal user, let's say you download the script to your home, in the terminal
```
./linux_recovery.sh

```

choose a recovery image, ZAKO would work (say it is #135, enter 135 after the prompt)


The script will run and then complain that there is no usb drive plugged in. just kill it.
Then navigate inside /tmp (open file manager, choose computer in the side pane, then find the tmp folder) to find a folder called crosre.tmp or something like that. Open it, copy the .bin file to somewhere in $HOME. This is the recovery image.

To mount the recovery image


```
sudo kpartx -av /path/to/bin/file

```It will print out a lot of partitions like


```
add map loop7p1 (253:0): 0 28672 linear 7:7 2928640
add map loop7p2 (253:1): 0 32768 linear 7:7 20480
add map loop7p3 (253:2): 0 2641920 linear 7:7 286720
add map loop7p4 (253:3): 0 32768 linear 7:7 53248
add map loop7p5 (253:4): 0 4096 linear 7:7 282624
add map loop7p6 (253:5): 0 1 linear 7:7 16448
add map loop7p7 (253:6): 0 1 linear 7:7 16449
add map loop7p8 (253:7): 0 32768 linear 7:7 86016
add map loop7p9 (253:8): 0 1 linear 7:7 16450
add map loop7p10 (253:9): 0 1 linear 7:7 16451
add map loop7p11 (253:10): 0 16384 linear 7:7 64
add map loop7p12 (253:11): 0 32768 linear 7:7 249856

```
You need the third one (corresponds to "ROOT" shown in file manager
To mount it (it doesn't open in file manager)

create a directory in your home to mount the image

```
mkdir mnt

```
mount the image to mnt
```

sudo mount -t ext2 /dev/mapper/loop7p3 -o ro  ~/mnt

```


navigate to mnt, now you will see the content of the partition you just mounted

inside mnt, navigate to  /opt/google/chrome/pepper/, libpepflashplayer.so is the flash that you need. Create a folder in your home called PepperFlash (say) then copy libpepflashplayer.so there


to unmount


```
sudo umount ~/mnt

```and


```
sudo kpartx -dv /path/to/bin/file

```

Now we need to configure freshplayerplugin to use ChromeOS' flash.  Let's create a .conf file for freshplayerplugin. When you installed freshplayerplugin, it installed a template for the config file, copy it to ~/.config, change the name by dropping .example

```
sudo cp /usr/share/doc/browser-plugin-freshplayer-pepperflash/freshwrapper.conf.example ~/.config/freshwrapper.conf

cd ~/.config
sudo chown  yourusername freshwrapper.conf

gedit freshwrapper.conf

```


Now edit freshwrapper.conf

in line 40, remove the # in front, and change pepperflash_path to the path where you put libpepflashplayer.so, in our example, it is in /home/yourusername/PepperFlash, so change this line to
```
pepperflash_path = "/home/yourusername/PepperFlash/libpepflashplayer.so"
``` 

then in line 46, change enable_3d to = 1

Save your edit.

Now restart Firefox and go to [here]("http://drmtest2.adobe.com:8080/SVP/SampleVideoPlayer_FP.html#") to do the adobe drm test

video for test [http://drmtest2.adobe.com:8080/Content/anonymous.f4v](http://drmtest2.adobe.com:8080/Content/anonymous.f4v)


Somehow cut and paste doesn't work on the test page,type in the test video's url manually.
The flash version from the ChromeOS recovery image is a bit behind, if you right click on a flash video it will show 25 even though Firefox's plugin page reports it as 26.

---

### Post by russkyca on 2017-07-15
> **AnupamMitra said:**
> Thanks, as advised I installed Windows Firefox in wine.What's the how-to for installing this?

> **deadflowr said:**
> Flash on linux no longer supports DRM-flash.
(Someday, maybe it'll make it back, but currently they had to remove that support in order to update flash for linux)

Alternatives would be to try and run something like Windows Firefox in wine.
Or any browser in a Windows virtual machine.Why is it still listed as if it works, then?
[http://get.adobe.com/flashplayer/about/](http://get.adobe.com/flashplayer/about/)

EDIT:   Oh, 'DRM-Flash?'

---

### Post by russkyca on 2017-07-15
Should I follow this?:
[https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)
[https://www.youtube.com/watch?v=bmA_Rug8koU](https://www.youtube.com/watch?v=bmA_Rug8koU)

Then install Firefox (for Windows)?   (Don't know how yet, though).

Is this method easier than the 'freshplayer plugin (install) way?;

---

### Post by monkeybrain20122 on 2017-07-15
> **russkyca said:**
> Should I follow this?:
[https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)
[https://www.youtube.com/watch?v=bmA_Rug8koU](https://www.youtube.com/watch?v=bmA_Rug8koU)

Then install Firefox (for Windows)?   (Don't know how yet, though).

Is this method easier than the 'freshplayer plugin (install) way?;


There are a few tricks for the wine method. First of all if you use wine you will most likely fail to install flash. The trick is to use playonlinux, set up a 32 bit wine prefix then install firefox and flash 32 bit into the same prefix (or install firefox in playonlinux, then check only the box shockwave player when prompted. there will be an error if you check flash) then there is a bug in wine that Firefox would not connect to the internet when restart. You have to go to about:config and change browser.tabs.remote.autostart2 to False. There are some other glitches associated with wine  like some windows not rendered properly, some foreign fonts may show up as gibberish etc.

The freshplayerplugin method is most elegant and it is not that hard following my step by step tutorial. It is seamless, doesn't involve wine and even hardware acceleration works.

---

### Post by deadflowr on 2017-07-15
I've always found linux mint's method of getting flash on wine to be one of the better methods:
[https://community.linuxmint.com/tutorial/view/2028]("https://community.linuxmint.com/tutorial/view/2028")

---

### Post by Dennis N on 2017-07-15
> The trick is to use playonlinux

I agree. I also installed Windows version of Firefox using Play On Linux back in January, but followed similar advice here from user autodave:

[https://ubuntuforums.org/showthread.php?t=2348795&p=13596670#post13596670](https://ubuntuforums.org/showthread.php?t=2348795&p=13596670#post13596670)

There is a difference in that user autodave said not to install shockwave; only install flash player, while user monkeybrain20122 says to install only shockwave. Maybe either will work but not both?

I also tried the Mint method before this, but for me it failed on the flash player install part.

Anyway, the final result met my expectations. I can login into the TV network websites with my cable provider password and watch content I am entitled to.

The next challenge for me was how to upgrade the flash player in Windows Firefox when the player starts getting blocked as out of date. Going directly to Adobe website to install flash only gave me an unspecified error. Finally succeeded, but only after a lot of trial and error with Play on Linux. Not obvious.

Good Luck

---

### Post by monkeybrain20122 on 2017-07-16
> **Dennis N said:**
> I 

The next challenge for me was how to upgrade the flash player in Windows Firefox when the player starts getting blocked as out of date. Going directly to Mozilla website to install flash only gave me an unspecified error. Finally succeeded, but only after a lot of trial and error with Play on Linux. Not obvious.


You can just download flash from Adobe, then use playonlinux to install it in the Wine prefix where FF is installed instead of doing it through Windows' FF. For a new install I found the most straight forward way is to set up an empty wine prefix first, down load flash and Windows FF separately and then install them one after the other to the same prefix (order doesn't matter) rather than trying to get playonlinux to fetch flash while installing FF.

But my recommendation is to use flash from Chromebook recovery image (not flash from Linux Chrome, it doesn't work for DRM) and freshplayerplugin like I posted above. It is the best and most elegant method and works much better than running FF in Wine. Wine is always the last option IMO.

---

### Post by Dennis N on 2017-07-16
> You can just download flash from Adobe, then use playonlinux to install it in the Wine prefix where FF is installed

Thanks. I will try that next time it needs replacement.

---

### Post by electrodan on 2018-05-16
Hello,

I thought I would post a follow up for those who come looking to get flash working.

The instructions monkeybrain20122 posted were very good and I used this method even in Ubuntu 18.04, however things evolved a little.

Firstly - it doesn't work in Firefox 60 (shows white screen where flash content should be), or Chromium (DRM error). I worked around this by installing Firefox ESR 52:

sudo add-apt-repository ppa:jonathonf/firefox-esr
sudo apt-get update
sudo apt-get install firefox-esr

It seems to work OK alongside Firefox 60, but don't run two at once.

Fresh player install has been updated, so instead of:
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt update
sudo apt install freshplayerplugin

Do this instead:
sudo apt-get install browser-plugin-freshplayer-pepperflash

For getting the libpepflashplayer.so the instructions worked great but note that ZAKO has moved so has a new ID. It has to be this one or you could get an incompatible ARM version.

I spent many hours trying to get it working in Firefox 60 or Chromium, and also hours trying to get Firefox and flash working well inside wine - all with no luck (not useful errors). So hope this helps someone!

---

### Post by monkeybrain20122 on 2018-05-17
> **electrodan said:**
> Hello,

Firstly - it doesn't work in Firefox 60 (shows white screen where flash content should be), or Chromium (DRM error). I worked around this by installing Firefox ESR 52:



Hi, 

It works on FF 60 here on Ubuntu 18.04. Problem is, as you observed correctly webupd8's freshplayerplugin is out of date (may not even be available for Ubuntu 18.04). FF made some changes around version 52 or 53 which broke freshplayer but it was fixed later. Not sure how old is "browser-plugin-freshplayer-pepperflash", probably still old if only works with FF-ESR. You need to compile freshplayerplugin from source for it to work for FF 60.

While bionic was late beta someone sent me a pm about this, here was the up to date instructions I cut and paste from my reply, still works:


So you'll have to compile flashplayer from source. The steps are also a  bit different from that forum post. You need to install chrome to get  its pepperflash  to "initialize" freshplayer (but it won't work on drm)  When all is done chrome can be removed and its copy of pepperflash  deleted.

1) Remove flash you have installed from the repo (adobe-flashplugin or  flashplugin-installer, something like that) and delete the  freshwrapper.conf you have created following the forum post

2) get chrome-book's image and extract flash as in the forum post. Put it somewhere, say /home/usr_name/PepperFlash

3) Download chrome. It seems that Chrome no longer bundles flash by default. In the url bar type about:components.  Check the flash tab, if it is a bunch of zeros that means it is not  installed, click update flash and it will download and install  pepperflash in your machine.
Note the full path of pepperflash it installs. On my machine it is

```
/home/monkeybrain/.config/google-chrome/PepperFlash/29.0.0.113/libpepflashplayer.so
```

**Edited: **the path for Chrome66 is now /home/monkeybrain/.config/google-chrome/PepperFlash/29.0.0.171/libpepflashplayer.so, also Chrome does download flash automatically, probably some glitches on my beta install back then.

4) compile freshplayerplugin.  

Download the source code as a zip file (click the green tab clone or download) [here]("https://github.com/i-rinat/freshplayerplugin"). .
Before you start compiling you need some build tools
```
sudo apt install build-essential cmake
``` 

Now just follow the instructions to install the prerequisites and go  through the build steps, they are pretty straight forward (just cmake  -options .. and make, don't do make install)

5) When you are done building. **Close firefox**. Open your  File manager, find the hidden file .mozilla , create a subfolder called  "plugins" (without quotes) inside. Now go in your freshplayerplugin  folder, inside the build folder you can find  libfreshwrapper-flashplayer.so, copy it to ~/.mozilla/plugins

6) Inside the freshplugin folder there is a subfolder called data.  Rename the file inside as freshwrapper.conf, open it with an editor, go  to line 40 pepperflash_path, remove the # in front and change the path  to where chrome installed its flash, in my case it is, as above
```
/home/monkeybrain/.config/google-chrome/PepperFlash/29.0.0.113/libpepflashplayer.so
```
change enable_3d to 1 (line 46)

7) copy the file from step 6 to ~/.config

8) Now open Firefox, go to Tools > Addons >  Plugins to check that flash is there, it should be version 29
Now freshplayer is initialized (at this point you can uninstall Chrome and delete the copy of pepperflash it installed) 

9) Close firefox, and edit freshwrapper.conf again, go to line 40 and  change the path to your chrome-ook flash in step 2. (you need to  initiaze freshplayerplugin because chrome-book's flash apparently has  different versioning, if you skip 6 -8 an go directly to 9 Firefox would  report flash version as 0.0.0.0 and none of the flash site would load)

10) start Firefox and do the drm test.


P.S Won't work for Chromium, I have asked the dev of freshplayerplugin.

---

### Post by electrodan on 2018-05-30
Thanks for your help.

I managed to get it to work in an acceptable fashion. An alternative to sort Firefox detecting the plugin as version 0.0.0.0 (which makes no flash content work) is copy manifest.json to the location of where I had copied the DRM version of Pepper Flash, in my case:
cp ~/.config/google-chrome/PepperFlash/29.0.0.171/manifest.json ~/PepperFlash/

Then after deleting pluginreg.dat from the Firefox profile directory - it shows a version now and works - so there was no need to initialise it back to the Google Chrome version.

In Firefox Quantum (I have version 60) though, the video performance is pretty poor (whereas in Firefox ESR is fine), until at least I make the video full screen - and then it is fine! It's a good 20 seconds or so before I can actually move the mouse to the full-screen button and I've not managed to solve that so I might still stick with Firefox ESR for now. If I do fix it I'll report back though. Computers with stronger processors may be fine though - I'm using a very cheap Celeron N3350 laptop for traveling with!

---

### Post by User-007 on 2018-07-08
Wow! Got it working on Mint 19, HBO Nordic works now.

Thanks a lot!

Regards 
User JB

---

### Post by Jan-Olof_Andersson on 2019-02-12
HBO Nordic now works great with 18.10 and Chrome. Just to run it!!! Finally

---

