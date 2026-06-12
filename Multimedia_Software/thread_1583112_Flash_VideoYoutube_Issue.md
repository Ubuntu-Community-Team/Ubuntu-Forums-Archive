---
title: "Flash Video/Youtube Issue"
date: 2010-09-27
forum: Multimedia Software
---

### Post by vipes27 on 2010-09-27
I having an issue watching flash movies and videos from youtube. It's fine the first time I watch a video, but if I go back or click on another video, it won't work. Typically, you get the "Play" triangle in the middle of the video after it loads. After the first video I watch, it's a very, very small "Play" triangle, and when I click on it, it does nothing. I always do the suggested updates, but maybe I'm still missing something. Also, if I close FireFox or Chrome (it happens on both) and go back to the site, I can play it fine the first time.

Thanks.

---

### Post by Cavsfan on 2010-09-27
see this link: [COLOR=RoyalBlue]_[http://ubuntuforums.org/showthread.php?t=1496785](http://ubuntuforums.org/showthread.php?t=1496785)_[/COLOR]

You should just need to do step 3.

---

### Post by vipes27 on 2010-09-27
Can you clarify something for me? 

When i copy this into the terminal:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
It automatically runs. 

I'm unsure where to put the last line of the post in:
Then add: export GDK_NATIVE_WINDOWS=1 before the last line of text

Do I put that all into the terminal?

Thanks again.

---

### Post by Cavsfan on 2010-09-27
> **vipes27 said:**
> Can you clarify something for me? 

When i copy this into the terminal:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
It automatically runs. 

I'm unsure where to put the last line of the post in:
Then add: export GDK_NATIVE_WINDOWS=1 before the last line of text

Do I put that all into the terminal?

Thanks again.

I am not real sure what happened, but I no longer have that file (/usr/lib/[COLOR=Red]nspluginwrapper[/COLOR]/i386/linux/npviewer)
The [COLOR=Red]nspluginwrapper[/COLOR] folder no longer exists.
I am using **Flash Player "Square" Preview Release** gotten from here: 
[[color=blue]_http://labs.adobe.com/downloads/flashplayer10.html_[/COLOR]](http://labs.adobe.com/downloads/flashplayer10.html)

I installed the 64 bit version and it works perfectly, but I am sure the 32 bit version will too if that is what your system is.
It has installation instructions on the page.

---

### Post by Cavsfan on 2010-09-27
I just did a search on the disk showing hidden files for ** libflashplayer.so** and replaced with the new downloaded one.

I believe that fix applied when I had the 32 bit Flash installed because there was no 64 bit flash available.

Then just restart your browser and it should work.

But, if you are using 32 bit and you do have that file - add **export GDK_NATIVE_WINDOWS=1** before the last line.

---

### Post by vipes27 on 2010-09-27
Thanks, Cavsfan, I'll try that when I get home.

I am using 32bit. Where exactly am I supposed add the export command? Is that in the terminal? I'm confused as to where, "before the last line," is. Sorry, I'm very new to Ubuntu.

---

### Post by Cavsfan on 2010-09-27
> **vipes27 said:**
> Thanks, Cavsfan, I'll try that when I get home.

I am using 32bit. Where exactly am I supposed add the export command? Is that in the terminal? I'm confused as to where, "before the last line," is. Sorry, I'm very new to Ubuntu.

When you enter that gksudo command in the terminal, it will ask for a password and then open up the file in gedit (text editor). 
That is where you will add that line just before the last line. And if you enter the gksudo command I mentioned and a blank screen 
opens up in gedit, it means you don't have the file. But, you probably do and just adding **export GDK_NATIVE_WINDOWS=1** before the last line should fix you up.

---

### Post by vipes27 on 2010-09-27
Thanks, that explains it. I did try it when I was home earlier and it brought up the text editor and it was blank, that's why I was confused where the last line was. I guess that means I don't have the file? If not, I'll just follow your instructions to download and install it.

---

### Post by Cavsfan on 2010-09-27
> **vipes27 said:**
> Thanks, that explains it. I did try it when I was home earlier and it brought up the text editor and it was blank, that's why I was confused where the last line was. I guess that means I don't have the file? If not, I'll just follow your instructions to download and install it.

That explains it! You don't have the file either. So, you can just install the 32 bit version  from that Adobe site I posted.

I just checked a YouTube video and it works great! I can stop, start, go into fullscreen and all the buttons work.
I guess they fixed that bug; there was a bug report also on the line with the fix.
That's good! :)

---

### Post by Cavsfan on 2010-09-27
Here is a good site to check what version of flash you are using - 
[[COLOR=blue]_http://www.adobe.com/software/flash/about/_[/COLOR]]("http://www.adobe.com/software/flash/about/")
It says the latest version is 10.1.85.3 but, since I am using the 64 bit "Square" Preview Release - it shows I have version 10,2,161,22 installed.

---

### Post by vipes27 on 2010-09-27
I checked and it showed I'm using 10.1.85.3.

I downloaded the file from your link, but I don't have an i386 folder inside of nspluginwrapper, just dirs.d. I did make sure that hidden files are shown, but it made no difference.

Any ideas?

---

### Post by Cavsfan on 2010-09-28
Here's my about : plugins in Firefox:

[[IMG]http://ompldr.org/tNW8xYg[/IMG]]("http://ompldr.org/vNW8xYg")

But, I am using 64 bit. You could try this from Mozzila's help:

[[COLOR=blue]_http://support.mozilla.com/en-US/kb/Managing+the+Flash+plugin?s=plugin+directory&as=s_[/COLOR]]("http://support.mozilla.com/en-US/kb/Managing+the+Flash+plugin?s=plugin+directory&as=s")

Just go to the Linux section towards the bottom. And you can use the file you already downloaded. 
Just restart your browser and enter **about : plugins** without the spaces and see what version is shows.

---

### Post by sticky_icky on 2010-10-28
**I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  **I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  

      I wish to christ i could have found this years ago...  i have the  same  problem, main monitor is 1440x900, running an xfx geforce 7600gt,  and  everything but youtube works.  flash/youtube/ubuntu=HUGE #$^@##@   headaches for years.  i tried litterally hundreds of workarounds or   fixes, HOURS of time trying to get the stupid flash fixed for more than 2   minutes, and not one single thing worked, ever, until now.t

      ubuntu forums had been completely useless to me, in those  endeavors,  wasted much time for nothing, though, in fairness to the  buntu, i fully  acknowledge the fruitful efforts of the ubuntu team, the  linux world has  made HUGE strides forward since i started with  slackware7.   with  ubuntu, the reality is that aside from arbitrary  reference, i haven't  needed the forums, everything but flash, some  really obscure software,  works like a charm, since the nvidia driver  issues have been  sorted.(btw, for me, the only way to install properly  working nvidia  drivers/nvidia settings/flashplugin is with apt from  terminal after  stopping gnome...**not with synaptic from the desktop**)

     since nothing's ever worked for me, i didn't bother reading the  thread, i'd be shocked if it was mentioned... anyway, after a routine  cleaning/reinstallation of firefox i happened across this:[ http://www.addonfox.com/]("http://www.addonfox.com/"),   which icludes some really good addons for firefox....also some bs, the   converter, swifclick, and windowshopper addons pissed me off...

the real gem of that collection, which i had never found before is:

**[flashvideoreplacer 1.0.5]("https://addons.mozilla.org/en-US/firefox/addon/161869/")**

      it "replaces embedded flash videos with quicktime or windows media   player compatible videos."   WHAT THAT MEANS IS IT COMPLETELY REPLACES   THE WHOLE, STUPID, YOUTUBE/GOOGLEVIDEO GUI AND **EMBEDS IN ITS PLACE MPLAYER**.
(in the preferences,the selection for plugin/mimeType, is "windows media player (application/x-mplayer2)

hall-o-fu#%ing-luja!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

     _**this is the only thing that has ever worked for me**_,   and it seems to be a really solid addon, so far as i can tell, not   buggy, video looks great-not choppy, options exist to automatically   choose the quality of youtube videos, choose cache size(default is   2megs), enable post processing, all the gnome mplayer interface   settings, etc.  _it doesn't seem to change anything on any video sites except youtube/googlevideos, and optionally vimeo and blip.tv etc._  only problem is i haven't been able to get the youtube playlist to autoplay the next vid.

if  you are frustrated wit yt/google, try this.  i can confir, it works   with gnome mplayer on 10.04.1 LTS.  i have every video and audio   application i could find, though, not sure of the impact other packages   have on mplayer/vice-versa.
[B]
hope this works for you, NO need to thank me if it does, but--

         PLEASE[/B] **PLEASE PLEASE help others when you have solutions.**

god bless.

---

### Post by Cavsfan on 2010-10-29
> **sticky_icky said:**
> **I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  **I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  

      I wish to christ i could have found this years ago...  i have the  same  problem, main monitor is 1440x900, running an xfx geforce 7600gt,  and  everything but youtube works.  flash/youtube/ubuntu=HUGE #$^@##@   headaches for years.  i tried litterally hundreds of workarounds or   fixes, HOURS of time trying to get the stupid flash fixed for more than 2   minutes, and not one single thing worked, ever, until now.t

      ubuntu forums had been completely useless to me, in those  endeavors,  wasted much time for nothing, though, in fairness to the  buntu, i fully  acknowledge the fruitful efforts of the ubuntu team, the  linux world has  made HUGE strides forward since i started with  slackware7.   with  ubuntu, the reality is that aside from arbitrary  reference, i haven't  needed the forums, everything but flash, some  really obscure software,  works like a charm, since the nvidia driver  issues have been  sorted.(btw, for me, the only way to install properly  working nvidia  drivers/nvidia settings/flashplugin is with apt from  terminal after  stopping gnome...**not with synaptic from the desktop**)

     since nothing's ever worked for me, i didn't bother reading the  thread, i'd be shocked if it was mentioned... anyway, after a routine  cleaning/reinstallation of firefox i happened across this:[ http://www.addonfox.com/]("http://www.addonfox.com/"),   which icludes some really good addons for firefox....also some bs, the   converter, swifclick, and windowshopper addons pissed me off...

the real gem of that collection, which i had never found before is:

**[flashvideoreplacer 1.0.5]("https://addons.mozilla.org/en-US/firefox/addon/161869/")**

      it "replaces embedded flash videos with quicktime or windows media   player compatible videos."   WHAT THAT MEANS IS IT COMPLETELY REPLACES   THE WHOLE, STUPID, YOUTUBE/GOOGLEVIDEO GUI AND **EMBEDS IN ITS PLACE MPLAYER**.
(in the preferences,the selection for plugin/mimeType, is "windows media player (application/x-mplayer2)

hall-o-fu#%ing-luja!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

     _**this is the only thing that has ever worked for me**_,   and it seems to be a really solid addon, so far as i can tell, not   buggy, video looks great-not choppy, options exist to automatically   choose the quality of youtube videos, choose cache size(default is   2megs), enable post processing, all the gnome mplayer interface   settings, etc.  _it doesn't seem to change anything on any video sites except youtube/googlevideos, and optionally vimeo and blip.tv etc._  only problem is i haven't been able to get the youtube playlist to autoplay the next vid.

if  you are frustrated wit yt/google, try this.  i can confir, it works   with gnome mplayer on 10.04.1 LTS.  i have every video and audio   application i could find, though, not sure of the impact other packages   have on mplayer/vice-versa.
[B]
hope this works for you, NO need to thank me if it does, but--

         PLEASE[/B] **PLEASE PLEASE help others when you have solutions.**

god bless.

That Firefox addon was authored by a member of this forum - **lovinglinux** and here is the link to one of his threads:
[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1491268&highlight=flashvideoreplacer_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1491268&highlight=flashvideoreplacer")
In his signature you will find several links to Firefox tutorials and other addons he has programmed.

You should have started your own thread on this issue and then waited patiently for a reply. If you have wasted 2 years finding a solution on your own, 
you would have been better off posting a new thread and waiting on a response to that thread. It might take a day or so for the right person, such as 
**lovinglinux** to find your thread and offer his help, but it will happen. I have seen it done. And I have benefited myself from the generosity of 
the people that are members of this great forum!  You will not find a better Ubuntu forum with more knowledgeable and generous people!

---

