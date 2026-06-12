---
title: "Amazon Instant Video"
date: 2012-12-28
forum: Multimedia Software
---

### Post by caffeinatedev on 2012-12-28
When trying to stream a movie with Amazon Instant Video, I am given an error message saying that my Flash player is unsupported (using Chrome browser 23.0.1271.97). It claims that I must either disable PPAPI or use a different browser. 

So I tried using Firefox (17.0.1) with the Adobe Flash plugin (11.2.202.258ubuntu0.12.04.1) from the Software Centre only to get an error message that says that either my browser or Flash player needs to be updated.

I'm using the latest version of the aforementioned software. I don't know what PPAPI is but I assume it's Chrome's Flash plugin.

---

### Post by caffeinatedev on 2012-12-28
I now realize that there are related threads on this topic but I want to post my solution anyway to save everyone else the trouble of searching all over the interwebz. :P

I found the problem to be that Amazon video streaming only works with Flash 11.2 and Chrome currently uses Flash 11.5. So I ran ```
sudo apt-get install hal
``` in the terminal and restarted Firefox. Streaming is working now but just in Firefox, it would be cool if someone could figure a way to get streaming working in Chrome.

---

### Post by sdowney717 on 2012-12-29
I can watch in chrome browser. Right click also shows flash 11.2


You can select somewhere in chrome between pepper 11.5 and adobe flash 11.2

---

### Post by caffeinatedev on 2013-01-03
In Chrome, type ```
about:plugins
``` in the address bar and disable Pepper (Flash 11.5).

---

### Post by topazhn on 2013-01-04
Hey All

Followed caffeinatedev's advice and got the Hardware Abstraction Layer (HAL). Now streaming Amazon.com instant videos in both Firefox & Chrome. Both browsers latest. Platform: 12.04 on Lenovo T400.

Thanks caffeinatedev

---

### Post by caffeinatedev on 2013-01-17
;) Anytime. If I saved you as much trouble as I hope I did then it was worth it.

---

### Post by sbrenneis on 2013-04-11
As of yesterday, Amazon requires a flash version newer than 11.2. Adobe says that 11.2 is the last supported version for Linux. Chrome uses 11.7, which I assume they are supporting themselves, but it has the DRM removed, so you can't use it (there are no other flash options in the latest version of chrome). Using firefox in wine works fine. The flash version there is also 11.7, but it is the windows supported version. As far as I can tell, firefox in wine is the only way you will be able to watch Amazon Instant on Linux. If anyone has an alternative, I would love to hear about it.

BTW, I already have HAL installed.

---

### Post by NatePiercy on 2013-04-14
Thanks, sbrenneis. I've been pretty frustrated the last 48 hours and wasn't sure whether this was a flash issue or a firefox issue. Windows in WINE it is. Great that there's a solution somewhere. :)

---

### Post by coldraven on 2013-04-14
For viewers in the UK installing hal is the only way you can watch 4OD.
One poster suggested that when 4OD detects a Linux system it should display a message telling you to install hal.
That would have saved me some hours of searching.

---

### Post by ginnyotte on 2013-04-14
I have installed hal, Amazon still does not work for me in Firefox.  In Chrome I get the message to d[COLOR=#000000][FONT=Verdana]isable PPAPI.  I have been trying for three days to get this to run, and to get Secnd Life to run; in both instances I have installed multiple versions, installed wine, installed nearly everything everyone has suggested and what worked for them and still nothing.  I feel stuck because since installing over Windows 8, I have no other OS to use any more AND I can no longer boot from a CD--even though I have my bios set to legacy mode so that I can boot froma CD, I can't any more.  I can't do anything with ubuntu expect post to facebook and use netflix.  It's maddening.  Why on Earth did I do this to myself?[/FONT][/COLOR]

---

### Post by utkjamie on 2013-04-30
Why is this thread marked "SOLVED" when the problem clearly has not been resolved? Needless to say I'm having the same problem with the latest Firefox, Flash and Ubuntu updates and after installing HAL.

---

### Post by topcoder on 2013-05-04
This solution worked for me: [http://askubuntu.com/questions/286297/is-there-a-work-around-to-get-amazon-prime-instant-videos-working](http://askubuntu.com/questions/286297/is-there-a-work-around-to-get-amazon-prime-instant-videos-working) (assumes that you have hal and hald installed)

```
sudo mkdir /etc/hal/fdi/preprobe
sudo mkdir /etc/hal/fdi/information
/usr/sbin/hald --daemon=yes --verbose=yes
rm -rf ~/.adobe
```

---

### Post by topcoder on 2013-05-04
BTW, I'm on Raring, not Lucid. Thanks to the Beans restriction, I cannot update my profile to indicate such.

---

### Post by utkjamie on 2013-05-04
> **topcoder said:**
> This solution worked for me: [http://askubuntu.com/questions/286297/is-there-a-work-around-to-get-amazon-prime-instant-videos-working](http://askubuntu.com/questions/286297/is-there-a-work-around-to-get-amazon-prime-instant-videos-working) (assumes that you have hal and hald installed)

```
sudo mkdir /etc/hal/fdi/preprobe
sudo mkdir /etc/hal/fdi/information
/usr/sbin/hald --daemon=yes --verbose=yes
rm -rf ~/.adobe
```

That worked! Thanks much!!

---

### Post by sabbyATL on 2013-06-06
> **topcoder said:**
> This solution worked for me: [http://askubuntu.com/questions/286297/is-there-a-work-around-to-get-amazon-prime-instant-videos-working](http://askubuntu.com/questions/286297/is-there-a-work-around-to-get-amazon-prime-instant-videos-working) (assumes that you have hal and hald installed)

```
sudo mkdir /etc/hal/fdi/preprobe
sudo mkdir /etc/hal/fdi/information
/usr/sbin/hald --daemon=yes --verbose=yes
rm -rf ~/.adobe
```


This worked great for me, also.  I am running 13.10 on a Toshiba Qosmio X505-Q8100X with 8G ram (not that all that detail is important).

---

### Post by alfick3 on 2013-06-22
So, I'm running Ubuntu 12.04 LTS on a HP with AMD Athlon(tm) II X2 255 Processor × 2, with VESA: RS880 graphics. I am using Chromium: Version 25.0.1364.160 Ubuntu 12.04 (25.0.1364.160-0ubuntu0.12.04.1). I also have Firefox 21.0. Until recently (sometime in the last couple of weeks, can't remember for sure when) I was able to watch Amazon Prime videos on Chromium. I still can on Firefox. When I try to use Chromium, I get a black screen; no error, no crash, just a black screen. I read somewhere it has to do with DRM, but can't find a new fix.

When I set up Chromium originally, several months ago when I first installed Ubuntu on my computer, I searched the forums and web and found out how to set it up and get it working. Now, I'm not finding anything new to help me out. I remember I tried out all three (FF, Chromium and Chrome), and chose Chromium as my default. I can't remember, now, why I chose Chromium over Chrome, but there musta' been a good reason, so I'd rather stick with Chromium. 


Like I said, I can still use FF, but I'd rather use Chromium (plus, it just bugs me that I can use one browser and not another. :D )

Any help would be appreciated.  Thanks.

Al

Edit: oh, also, this affects playing music from Google Play. I can no longer play my music. I do get a message saying that I should refresh or update flash player. But again, I can still play it from Firefox.

---

### Post by alfick3 on 2013-06-22
Bump, Any one have any ideas?

---

### Post by riesengreen on 2013-07-06
Hi All:

I have found the following answer to my problem--I can't watch Amazon Instant Videos with Firefox 22.0 on ubuntu 13.04. It is to run the following commands in a terminal. 

sudo mkdir /etc/hal/fdi/preprobe
sudo mkdir /etc/hal/fdi/information
/usr/sbin/hald --daemon=yes --verbose=yes
rm -rf ~/.adobe

Seems like lots of folks have used these and they work. I'm ready to do the same, but it's just that...well...I'd like to know what exactly it is that I am doing. I'd like to ask the following:

1) Am I correct in thinking that each line is a command to be entered in the terminal, followed by the enter key and my password?
2) What does each command do? Even a broad outline would make me feel better about entering what are--to me--unintelligible lines of code into my terminal.

I appreciate all the help I've received here. If anybody has anything for me on this, thanks again!

---

### Post by pvfjr on 2013-07-08
The fix just worked for me.  I had to preceed it with ```
sudo apt-get install hal
```
The first mkdir lines did nothing, the files already existed.  The next two must have fixed it for me.

---

### Post by mark2741 on 2013-07-08
Me too. Installing just hal did not.

I'm on Ubuntu 13.04 64-bit. Chrome browser.

---

### Post by andyg0808 on 2013-07-10
> **riesengreen said:**
> Hi All:

I have found the following answer to my problem--I can't watch Amazon Instant Videos with Firefox 22.0 on ubuntu 13.04. It is to run the following commands in a terminal. 

sudo mkdir /etc/hal/fdi/preprobe
sudo mkdir /etc/hal/fdi/information
/usr/sbin/hald --daemon=yes --verbose=yes
rm -rf ~/.adobe

Seems like lots of folks have used these and they work. I'm ready to do the same, but it's just that...well...I'd like to know what exactly it is that I am doing. I'd like to ask the following:

1) Am I correct in thinking that each line is a command to be entered in the terminal, followed by the enter key and my password?
2) What does each command do? Even a broad outline would make me feel better about entering what are--to me--unintelligible lines of code into my terminal.

I appreciate all the help I've received here. If anybody has anything for me on this, thanks again!

To answer #1, yes, those are commands and you'll need to enter them in the terminal, using enter to run each line. Your password will be requested for the first [FONT=courier new]sudo[/FONT], but will (usually) be remembered for the second.

To answer #2:
[FONT=courier new]sudo mkdir /etc/hal/fdi/preprobe[/FONT] creates a directory [FONT=courier new]preprobe[/FONT] in [FONT=courier new]/etc/hal/fdi/[/FONT]; the next line also creates a directory.
I don't know what the third line does, but in the spirit of teaching a man to fish, I'll show you how to find out:
[LIST=1]
[*]The first part of the line ([FONT=courier new]/usr/sbin/hald[/FONT]) is the path to a program to run, in this case, [FONT=courier new]hald[/FONT].
[*]Using that name, we can find out what the command does by typing [FONT=courier new]man hald[/FONT] in a terminal and pressing enter. A "manpage" should appear, providing information about the command. Check Wikipedia for more on manpages.
[/LIST]
The fourth line deletes the hidden directory [FONT=courier new].adobe[/FONT] in your home directory. In *nix, a dot at the beginning of a file/directory name generally hides the item. [FONT=courier new]rm -rf[/FONT] recursively deletes a directory and forces deletion of all its contents. As with [FONT=courier new]hald[/FONT] (and [FONT=courier new]mkdir[/FONT] and [FONT=courier new]sudo[/FONT]), you can use [FONT=courier new]man rm[/FONT] to find out more about the [FONT=courier new]rm[/FONT] command.

A quick personal note: If you're not familiar with the terminal, it's well worth getting acquainted. It's super-powerful!

---

### Post by topcoder on 2013-10-20
hal is not available in saucy (13.10). The solution that worked for me was to download [libhal-storage1]("http://packages.ubuntu.com/raring/libhal-storage1") and [hal]("http://packages.ubuntu.com/raring/hal") from the raring repositories.

---

### Post by SeijiSensei on 2013-10-20
Hmm.  That makes sense, but it didn't work for me.  I installed the 0.5.14-8ubuntu1 packages for HAL from Saucy but still get the flashplayer is out of date message.  I also had to install libhal1 since libhal1-storage requires it.  Did you also downgrade the Flash Player package?  I use the partner repositories to install Flash; my version is 11.2.202.310-0raring1.  How about you?

It would be nice if we could resolve this without needing changes to the Saucy repository.  My [conversation with the developers]("https://answers.launchpad.net/ubuntu/+source/hal/+question/237614") so far has not been very encouraging.

---

### Post by SeijiSensei on 2013-10-20
I have since tried removing the contents of ~/.adobe which was suggested in [this post](http://ubuntuforums.org/showthread.php?t=1987855&p=12822596#post12822596).  I started *Pi* because it was the first item on the Prime Instant Video page.  Now I see the first couple seconds of the film (the Lionsgate logo), but again the player crashes with the "out-of-date" message.  Better, but not a solution yet.

---

### Post by aperomsik on 2013-10-27
Someone posted an updated hal for saucy in a ppa, which I found linked in a [different thread]("http://ubuntuforums.org/showthread.php?t=2144347&p=12822755&viewfull=1#post12822755"). Seems to work.

---

### Post by dwlewi4 on 2014-01-01
> **aperomsik said:**
> Someone posted an updated hal for saucy in a ppa, which I found linked in a [different thread]("http://ubuntuforums.org/showthread.php?t=2144347&p=12822755&viewfull=1#post12822755"). Seems to work.

Only this would work for me.  Firefox now playing amazon instant in 13.10

---

