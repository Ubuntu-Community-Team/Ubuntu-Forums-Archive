---
title: "Flash not working (only in Youtube)"
date: 2009-10-02
forum: Multimedia Software
---

### Post by feelshift on 2009-10-02
Hi, I have a really annoying problem with flash player in Firefox. It works just fine but then Youtube displays "An error occurred, please try again later.".
The strange thing is that it only happens on Youtube, other flash using websites work. Clearing the cache resolves the problem, but I have auto-login enable on many sites and I don't want to lose this option every time Youtube stops working.

I manually deleted several video files from the cache folder but not when I try to play a video on their site it doesn't even display the error message (the embed ones do).

Youtube works flawlessly in Epiphany.

I tried reinstalling flash without any effect. This thing has happened on other Jaunty installations too.

Any suggestions? :confused:

---

### Post by ajgreeny on 2009-10-02
What flash packages have you installed?  There are many instances of problems if other apps such as gnash or swfdec are installed as well as adobe flash, so if you have anything other than the adobe version, I suggest you uninstall it.

---

### Post by feelshift on 2009-10-03
I have installed only the adobe version.

---

### Post by feelshift on 2009-10-03
For no apparent reason Youtube displays again "An error occurred, please try again later." :confused:

---

### Post by feelshift on 2009-10-04
Bump

---

### Post by ikacer on 2009-10-04
I suggest you try this thread:

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by feelshift on 2009-10-05
> **ikacer said:**
> I suggest you try this thread:

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

Clearing the cookies solves the problem, so I think this is more of a compatibility problem between Firefox, Youtube and Adobe Flash Player. I keep noticing that Youtube stops playing video after two or three days (it may depend on the number the videos I viewed).

---

### Post by feelshift on 2009-12-31
In Firefox: Edit -> Preferences -> Privacy -> "remove individual cookies" search youtube.com and remove all its cookies (leave LOGIN_INFO if you have enabled auto login). :popcorn:

---

### Post by anystupidname1 on 2010-04-16
I'm having to clear the cookies for EVERY youtube video I watch. This is not usable...
-Goto youtube
-Clear youtube cookies
-Reload page
-Watch video
-Try to go to next video
-"An error occurred, please try again later."
-Clear youtube cookies
-Reload page
-Watch video
-Try to go to next video
-"An error occurred, please try again later."
-Clear youtube cookies
 -Reload page
-Watch video

---

### Post by feelshift on 2010-04-17
> **anystupidname1 said:**
> I'm having to clear the cookies for EVERY youtube video I watch. This is not usable...
-Goto youtube
-Clear youtube cookies
-Reload page
-Watch video
-Try to go to next video
-"An error occurred, please try again later."
-Clear youtube cookies
-Reload page
-Watch video
-Try to go to next video
-"An error occurred, please try again later."
-Clear youtube cookies
 -Reload page
-Watch video

It works for me since I watch 15-20 videos before I have to do it again.

---

### Post by werewolfy on 2010-04-26
> **anystupidname1 said:**
> I'm having to clear the cookies for EVERY youtube video I watch. This is not usable...
-Goto youtube
-Clear youtube cookies
-Reload page
-Watch video
-Try to go to next video
-"An error occurred, please try again later."
-Clear youtube cookies
-Reload page
-Watch video
-Try to go to next video
-"An error occurred, please try again later."
-Clear youtube cookies
 -Reload page
-Watch video

* Install "privoxy" ( [http://www.privoxy.org/](http://www.privoxy.org/) )

* Add this to the file "user.action" (search for it or look in the privoxy manuals where to find the config files):

# Youtube error
{ +crunch-all-cookies }
.youtube.com

This will crunch all youtube-cookies for you.

* Instruct your browser to use "privoxy" as proxy:
for HTTP and HTTPS set the following (it depends on your browser where to do this, usually there is something called "network" or similar in the setup):

adress:  127.0.0.1    port: 8118

Read the privoxy manual for more info.

* If privoxy is already running, restart it with
sudo /etc/init.d/privoxy restart
or restart the service via the GUI or - if that's all too involved -simply reboot.


I recommend using Opera or Firefox as browser, which both have simple means to turn on and off the proxy if necessary. I do prefer Opera.

BTW, this is not only valid for all Linux distris but for all recent Windows versions as well!

And you can do a lot more with "privoxy", e.g. filtering ads ad banners (it's already set up to do a lot of that after installation) etc.

---

### Post by Mightymatze on 2010-04-30
hiho.  just block all cookies for youtube in your browser settings.

---

### Post by popsz on 2010-05-19
That worked!  Just deleting the cookies didn't work, but as soon as I deleted the ones I had and then put a block on cookies from youtube, the videos began to play.  uh... Pass the popcorn please.  :)

---

### Post by mleidel on 2010-08-01
I'm using Ubuntu 10.04 LTS. You-Tube videos did not work after the initial Ubuntu upgrade.
I used the FireFox extension **"Flash-Aid"**. It downloaded and correctly installed Flash...
You-Tube works fine now.

---

### Post by mleidel on 2010-08-02
See my solution.. #14 in this thread.

---

### Post by klEEh on 2010-08-18
> **mleidel said:**
> See my solution.. #14 in this thread.

Nice dude=D>. Youtube and other videosites stopped suddenly stopped working. Tried your solution (nearly gave up, nothing seemed to be able to fix this) and bingo! ;) I was because flash doesn't support 64-bit anymore, then it just installed the 32-bit version and here we go ;)

Thanks. :popcorn:

---

### Post by duongnn on 2010-10-21
Thanks.
You help me out of the same problem.

---

### Post by searkitguy on 2011-07-07
i uninstalled the updated flashplayer and reinstalled flashplayer 10, works normally now.:popcorn:

---

### Post by lovinglinux on 2011-07-07
See [YouTube Problems Mega Thread]("http://ubuntuforums.org/showthread.php?t=1799217")

---

