---
title: "Flash video freezes in fullscreen, sound continues"
date: 2010-10-11
forum: Multimedia Software
---

### Post by JakP on 2010-10-11
Have just upgraded to 10.10 using update manager, using firefox playing flash videos works fine untill i try to watch in fullscreen where the video freezes every few minutes although the sound keeps playing.

toshiba satellite laptop using Intel,  GMA 4500MHD

Anything anyone can suggest to solve this would be appreciated, really don't won't to have to re-install 10.04 if i can avoid it

many thanks

---

### Post by Dans564 on 2010-10-11
Same problem here.  It also happens when the matrix screensaver is on for a bit.  Any gotta fix.  

It has become so annoying I'm on windows right now! PLEASE SAVE ME!

Custom PC with 2X gtx 460 in sli, i5-760, p7p55d-evo mb

---

### Post by Dans564 on 2010-10-11
> **Dans564 said:**
> Same problem here.  It also happens when the matrix screensaver is on for a bit.  Any gotta fix.  

It has become so annoying I'm on windows right now! PLEASE SAVE ME!

Custom PC with 2X gtx 460 in sli, i5-760, p7p55d-evo mb

oh yea im in 10.10 as well

---

### Post by lovinglinux on 2010-10-11
Try these:

[Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

[Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

### Post by Dans564 on 2010-10-11
thanks for the suggestion, although I don't believe that the screen saver uses flash.  It might be two different problems, but they look awfully similar.  To me they seem to be the same problem, just two different instances.  I have a feeling it has something to do with the X-server.

---

### Post by lovinglinux on 2010-10-11
> **Dans564 said:**
> thanks for the suggestion, although I don't believe that the screen saver uses flash.  It might be two different problems, but they look awfully similar.  To me they seem to be the same problem, just two different instances.  I have a feeling it has something to do with the X-server.

Do you have the latest driver for your video card?

---

### Post by Dans564 on 2010-10-11
yea i had the newest one from the repos. I just did a fresh install. it seems to have fixed it.  thanks for the help anyways.
I was remembering the problems seemed to have started when i installed KDE onto Ubuntu.  :/ don't know what that means, but its interesting.

---

### Post by DrDmoney on 2010-10-11
I am having thes same problem on a clean install. I have the same hardware, and been looking for a fix. I have used ubuntu many times, but I always go back to windows for small error like this that I have no idea how to fix. I just want to get it working right so I can stay.

---

### Post by lovinglinux on 2010-10-11
> **DrDmoney said:**
> I am having thes same problem on a clean install. I have the same hardware, and been looking for a fix. I have used ubuntu many times, but I always go back to windows for small error like this that I have no idea how to fix. I just want to get it working right so I can stay.

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by DrDmoney on 2010-10-11
Shockwave Flash 10.1 r85

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.10) Gecko/20100922 Ubuntu/10.10 (maverick) Firefox/3.6.10

```
Ubuntu Architecture

Linux mooney-TM 2.6.35-22-generic-pae #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox                        install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.10/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources


Flash packages

flashplugin-installer                install

Plugin locations



Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)


```

I have done a fresh install again and didn't install any other software, to eliminate other variables. Could this be a driver issue with my graphics card?

---

### Post by JakP on 2010-10-12
Many thanks to lovinglinux, first link seems to have fixed this for me:

sudo mkdir /etc/adobe 
echo "OverrideGPUValidation=true" >~/mms.cfg 
sudo mv ~/mms.cfg /etc/adobe/

you're a wonderful humanbeing and will recieve my undying gratitude

---

### Post by dbd on 2010-10-12
> **JakP said:**
> Many thanks to lovinglinux, first link seems to have fixed this for me:

sudo mkdir /etc/adobe 
echo "OverrideGPUValidation=true" >~/mms.cfg 
sudo mv ~/mms.cfg /etc/adobe/

you're a wonderful humanbeing and will recieve my undying gratitude

I had exactly the same problem, and that fix worked perfectly for me too. Thanks lovinglinux, and JakP :)

---

### Post by lovinglinux on 2010-10-12
> **JakP said:**
> Many thanks to lovinglinux, first link seems to have fixed this for me:

sudo mkdir /etc/adobe 
echo "OverrideGPUValidation=true" >~/mms.cfg 
sudo mv ~/mms.cfg /etc/adobe/

you're a wonderful humanbeing and will recieve my undying gratitude

> **dbd said:**
> I had exactly the same problem, and that fix worked perfectly for me too. Thanks lovinglinux, and JakP :)

You are welcome.

> **DrDmoney said:**
> Shockwave Flash 10.1 r85

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.10) Gecko/20100922 Ubuntu/10.10 (maverick) Firefox/3.6.10

I have done a fresh install again and didn't install any other software, to eliminate other variables. Could this be a driver issue with my graphics card?

Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

---

### Post by DrDmoney on 2010-10-12
> **lovinglinux said:**
> You are welcome.



Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.
flash aid did the trick, but videos at high resolution are choppy, much so at 1080p in full-screen. Now i know that my Intel gpu sucks ***, but on windows and fedora my video playback are perfect. But at-least we got it. Thank you

---

### Post by lovinglinux on 2010-10-12
> **DrDmoney said:**
> flash aid did the trick, but videos at high resolution are choppy, much so at 1080p in full-screen. Now i know that my Intel gpu sucks ***, but on windows and fedora my video playback are perfect. But at-least we got it. Thank you

Then get [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/161869/"). At least you will be able to watch HD videos on YouTube. I'm the developer of that extension too.

---

### Post by DrDmoney on 2010-10-12
That did the trick... Much clearer video quality. Thank you so much for all your help. Does this interfere with youtube god awful  ads, other than not play them.

---

### Post by lovinglinux on 2010-10-12
> **DrDmoney said:**
> That did the trick... Much clearer video quality. Thank you so much for all your help.

That was fast. 

You are welcome.

---

### Post by Kuzma86 on 2010-10-19
YESSSS! Finally the stupid full screen freeze is gone!

---

### Post by kernelles on 2010-10-19
I have the same problem since I installed 10.10. My hardware is a Dell Inspiron 640m laptop. I ran 10.04 since April, with no problems in flash, so this is definitely related to something in 10.10, rather than my machine. Another difference is I did not just upgrade, I did a fresh install. For me, the problem is intermittent. It freezes the video maybe 75% of the time when fullscreen is selected.

---

### Post by hadrons123 on 2010-10-23
thanks.....The screen doesnt freeze but i got a different problem.the minimized flash box  is blank and it doesnt show any video anymore,but i can hear the sound.Do u know why?  i use compiz,by the way.it doesnt happen in metacity.

---

### Post by lovinglinux on 2010-10-23
> **hadrons123 said:**
> thanks.....The screen doesnt freeze but i got a different problem.the minimized flash box  is blank and it doesnt show any video anymore,but i can hear the sound.Do u know why?  i use compiz,by the way.it doesnt happen in metacity.

What have you done so far?

---

### Post by firstc624 on 2010-10-23
Ok what about if using Chrome?  it does the same thing.  That is my issue.  I use chrome but flash freezes full screen here as well

---

### Post by lovinglinux on 2010-10-23
> **firstc624 said:**
> Ok what about if using Chrome?  it does the same thing.  That is my issue.  I use chrome but flash freezes full screen here as well

Have you done anything suggested in this thread to try to fix this?

---

### Post by kamitsukai on 2010-10-24
> 
sudo mkdir /etc/adobe 
echo "OverrideGPUValidation=true" >~/mms.cfg 
sudo mv ~/mms.cfg /etc/adobe/


Thanks this fixed the same fullscreen flash problem for me on Mint 10

---

### Post by hadrons123 on 2010-10-25
> **lovinglinux said:**
> What have you done so far?


I 've done this 

sudo mkdir /etc/adobe 
echo "OverrideGPUValidation=true" >~/mms.cfg 
sudo mv ~/mms.cfg /etc/adobe/


The frozen fullscreen issue is solved.But the flash video quality is much reduced.I think poor video rendering right now compared to unfixed state.I have a ATI X1400 GPU in my E1505 dell notebook.During full screen flash video playing initially I had band of white lines running in the bottom of the screen on and off.Running flash totally eats up almost all of cpu.using chrome or latest minefield crawls thereafter.only closing the offending flash tab solves the cpu hog.

---

### Post by Laer899 on 2010-10-25
> **dbd said:**
> I had exactly the same problem, and that fix worked perfectly for me too. Thanks lovinglinux, and JakP :)

I was another with this same issue and the gma 4500mhd graphics. This worked for me as well. Much thanks!!!

---

### Post by lovinglinux on 2010-10-25
> **hadrons123 said:**
> I 've done this 

sudo mkdir /etc/adobe 
echo "OverrideGPUValidation=true" >~/mms.cfg 
sudo mv ~/mms.cfg /etc/adobe/


The frozen fullscreen issue is solved.But the flash video quality is much reduced.I think poor video rendering right now compared to unfixed state.I have a ATI X1400 GPU in my E1505 dell notebook.During full screen flash video playing initially I had band of white lines running in the bottom of the screen on and off.Running flash totally eats up almost all of cpu.using chrome or latest minefield crawls thereafter.only closing the offending flash tab solves the cpu hog.

You could try to undo that and disable Compiz.

---

### Post by firstc624 on 2010-10-25
> **kamitsukai said:**
> Thanks this fixed the same fullscreen flash problem for me on Mint 10

Sorry for the delay in answering.  This worked for me as well.

---

### Post by hadrons123 on 2010-10-26
> **lovinglinux said:**
> You could try to undo that and disable Compiz.

I dont know how to undo that change.I dont know the specific commands.

---

### Post by lovinglinux on 2010-10-26
> **hadrons123 said:**
> I dont know how to undo that change.I dont know the specific commands.

```
sudo rm -f /etc/adobe/mms.cfg
```

---

### Post by hadrons123 on 2010-10-27
> **lovinglinux said:**
> ```
sudo rm -f /etc/adobe/mms.cfg
```

Thanks!

---

### Post by stfnvgt on 2010-11-07
The same issue here with Dell Inspiron 1525, have not find a fix jet

---

### Post by rakete on 2010-11-09
> sudo mkdir /etc/adobe 
echo "OverrideGPUValidation=true" >~/mms.cfg 
sudo mv ~/mms.cfg /etc/adobe/                      fixed the issue for me too with firefox and chromium on a Dell Latittude E5410 with Intel HD Graphics.

the CPU has now a workload of 25% to 30% for all four CPU Threads (Core i5-520M), when playing a flash movie on youtube. 

So this fix seems to be no solution for slower CPU's... :(

---

### Post by Nencio on 2010-11-11
After I upgraded to 10.10 from 10.04 I started to have the same issue: frozen screen but audio going when watching falsh videos fullscreen.

The suggested workaround

> sudo mkdir /etc/adobe 
echo "OverrideGPUValidation=true" >~/mms.cfg 
sudo mv ~/mms.cfg /etc/adobe/                      fixed the problem for me. I'm running ubuntu on a HP pavillion dv6500 laptop.

Thanks a lot.

---

### Post by Merlin2007 on 2010-11-11
[B][B]This trick worked for my HP Media Centre PC m7060n with Ubuntu Maverick 10.10 32 bit Desktop Edition
[/B][/B]
**Overriding GPU validation**

If the above trick does not work, here&#8217;s what you can do:
Open a terminal and type the following command:

sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/

Start your browser and play the video in full screen. It should work now.

I then right clicked the video in Youtube and 
re-enabled hardware acceleration
and now I have full screen video.

Thanks go to:
[http://maketecheasier.com/play-youtube-video-fullscreen-youtube-video-in-ubuntu-maverick-10-10-try-this-fix/2010/11/10](http://maketecheasier.com/play-youtube-video-fullscreen-youtube-video-in-ubuntu-maverick-10-10-try-this-fix/2010/11/10)


for pointing the required solution to my dilemma.

---

### Post by beew on 2010-11-11
I tried that trick but the effect was negligible.  The only thing that works on my rather modest machine (2GH cpu, 1 G of ram) is to do away with flash altogether if I want to watch 720p.

 If you use FireFox Lovinglinux's flashvideoreplacer absolutely rocks (at least on machines with >=1G of ram. I am still trying to get mplayer to play 720p with 512M of ram :)). Otherwise you can install minitube which is also excellent. Both work well even with Compiz on!

---

### Post by myolbug on 2010-11-22
I am going to ask here, as my previous request in a different thread hasn't been answered.

I have Mint 10 64bit upgraded to the DVD version.  I haven't been able to play YouTube normally yet.  Compiz is on, but I have it on on Mint 9 and YouTube works fine.  (Same laptop)

I can click on the invisible full screen button and watch it in full screen but no dice on normal.

---

### Post by myolbug on 2010-11-22
> **kamitsukai said:**
> Thanks this fixed the same fullscreen flash problem for me on Mint 10

Were you ever able to get YT to work normally?  I have yet to get it to work.

---

### Post by myolbug on 2010-11-24
Ne1?

---

### Post by aditya.sharma on 2010-11-25
> **myolbug said:**
> Ne1?

I was facing similar issues but I got the choppy videos only once I resumed after suspending my laptop. I was able to get fullscreen flash to work correctly after executing these commands mentioned in this same thread:


```

sudo mkdir /etc/adobe 
echo "OverrideGPUValidation=true" >~/mms.cfg 
sudo mv ~/mms.cfg /etc/adobe/

```

---

### Post by DrDmoney on 2010-11-27
What I think the strangest thing about my situation is that after breaking in a new installation Ubuntu flash playback fixes itself. I don't know how it does it, but it just does. I just did a reinstallion of ubuntu, and lets hope it fixes itself again...

---

### Post by jhomie1 on 2010-11-27
Right click on the screen you are playing for example any video you choose on youtube.com  and click settings then uncheck hardware acceleration. that should do the trick. hope this helps.:D

---

### Post by Ecip on 2011-01-05
thank you, i solved my problem with videos freezing in fullscreen as per this site and the advice in this threat:

[http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10](http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10)

---

### Post by imixmuan on 2011-01-22
Noobie (ubuntu 10.10 on a dell latittude d620) trying to solve Flash freezing issue with a potentially stupid question:

I open a terminal and type in the command:

sudo mkdir /etc/adobe hit enter and get " file or directory exists" and new prompt line

I try copy and pasting full command text into the terminal window and still get same message. Do I need to delete the adobe file in /etc before trying to enter commands? Am I not running as root and that's the issue?

apologies if above is noob mistake

---

### Post by Nencio on 2011-01-23
> 
sudo mkdir /etc/adobe hit enter and get " file or directory exists" and new prompt line
mkdir is used to create new directories. The message you get does mean exactly what it says. You can check if the /etc/adobe directory already exists with the command
```

ls /etc

```which will list all the directories inside /etc. see if adobe is in that list. if it does so, then just simply try the other two commands from the work around:
> 
 echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
The first one creates a text file called mms.cfg, which contains the string "OverrideGPUValidation=true", in your current directory ~.
The second one move the file to the /etc/adobe directory.

---

### Post by lovinglinux on 2011-01-23
> **imixmuan said:**
> Noobie (ubuntu 10.10 on a dell latittude d620) trying to solve Flash freezing issue with a potentially stupid question:

I open a terminal and type in the command:

sudo mkdir /etc/adobe hit enter and get " file or directory exists" and new prompt line

I try copy and pasting full command text into the terminal window and still get same message. Do I need to delete the adobe file in /etc before trying to enter commands? Am I not running as root and that's the issue?

apologies if above is noob mistake

Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and run it. It will apply that tweak if not present, will remove conflicting plugins and install the latest beta, according to your system architecture and version.

---

### Post by technocp on 2011-03-10
> **lovinglinux said:**
> Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

I dont know what you were trying to do out of that but when I changed plugin.expose_full_path to true every thing went OK and now I am able to see my videos in full screen.

Thanks :D

---

### Post by masajimckee on 2011-03-19
is something supposed to happen when you do these commands... mine is the same as the noob(also a noob) and when I typed in those two commands they didn't do anything.

---

### Post by Pulvret on 2011-06-12
I had the same problem and I fixed it by turning off feh which I used to view backgrounds.

---

### Post by akiragtr on 2011-07-25
Worked for me! Thanks

---

### Post by sudomp on 2011-09-10
Thanks!

---

### Post by peshwa on 2011-09-24
Hi, 
  I had the same Flash Full Screen Freeze issue on my Ubuntu 10.10. In my case none of the above links or suggestions worked.

   What worked was: disable Adblock Plugin. 

   Flash video full screen now works again. I got this solution from the[ list of problematic extensions on Firefox webpage.]("http://www.webgapps.org/tutorials/firefox/optimization/extension-optimization")  There are some excellent suggestions there to try out.

Cheers

---

### Post by avspavan on 2011-12-29
Hi,

My Dell XPSM1330 has the similar problem. What I see is that the full screen works for 20-30 mins and then it starts playing in frames..all the way to 1 frame/sec and finally to complete freeze. I moved from Ubuntu 11.10 to 10.10 but no luck. My laptop config is below. Can someone let me know if there is a fix for this? I am a novice at Linux OS. So please be detailed. 

Thanks,
Pavan

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
stepping	: 13
cpu MHz		: 800.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority
bogomips	: 3988.42
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
stepping	: 13
cpu MHz		: 800.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority
bogomips	: 3988.84
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

---

### Post by vangop on 2012-01-01
It must be something wrong with FF. Since flash vids are working fine in chrome.
I tried all the suggestions, but none of them worked so far. Can't try the old trick with disable HW acceleration, since when I right click->settings the dialog is not responding to mouseclicks.
 Have to watch youtube in chrome.

---

### Post by lovinglinux on 2012-01-01
> **vangop said:**
> It must be something wrong with FF. Since flash vids are working fine in chrome.
I tried all the suggestions, but none of them worked so far. Can't try the old trick with disable HW acceleration, since when I right click->settings the dialog is not responding to mouseclicks.
 Have to watch youtube in chrome.

Have you tried [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)?

---

### Post by boz86 on 2012-01-13
> **lovinglinux said:**
> Have you tried [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")?

I've tried all of these suggestions with no luck. Dell Inspiron 1520, 2 gb ram,  [FONT=monospace]nVidia Corporation G86 [GeForce 8400M GS][/FONT] graphics card.

Appreciate any more ideas, because I'd really like to neck down to one OS.

---

### Post by vangop on 2012-01-14
> **lovinglinux said:**
> Have you tried [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)?
Yes, didn't help.
It seems that the freeze is happening always for some vids, never happen for other..

---

### Post by rulet on 2012-03-28
Confirm this bug on Ubuntu 11.10 32 bit, flash video freeze in firefox on fullscreen with the latest adobe flashplugin when playing 1080p. It is on nvidia videocard.
Flashplugin was installed from canonical's partner repository.
The same bug was on the previouse version of flashplugin with a different nvidia card. There is no such bug on debian 6 stable with the latest adobe flashplugin installed.

 ... But, anyway I don't care much about it, flash is dying, and so be. A lot of flash-videos already replaced by html5-videos.

---

### Post by lovinglinux on 2012-03-31
> **vangop said:**
> It must be something wrong with FF. Since flash vids are working fine in chrome.
I tried all the suggestions, but none of them worked so far. Can't try the old trick with disable HW acceleration, since when I right click->settings the dialog is not responding to mouseclicks.
 Have to watch youtube in chrome.

Try to delete the flash config file:

```
sudo rm -f /etc/adobe/mms.cfg
```

---

