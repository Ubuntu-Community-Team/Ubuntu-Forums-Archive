---
title: "Can't stream live video from nbcolympics.com on Ubuntu"
date: 2016-08-07
forum: Multimedia Software
---

### Post by findlj52 on 2016-08-07
Hello,   I'm running Ubuntu 14.04 with adode flash installed.  the plugin installer version is 11.2.202.632.   However, streaming video from the 2016 olympics will not run.  After clicking on any of the live stream videos,  I'm prompted for my  login info from my TV provider, which I give accurately, I'll get the spinning dial of the video trying to load and then in a short while I'm prompted again for the sign in.   I know the login to the TV provider is correct because I can stream from my mac fine.   I've also installed the Lightspark video player but it acts the same.  

Note that I did not remove the Adobe flash player after installing Lightspark.

Has anyone gotten the live streaming from this Olympics  to work with their Ubuntu or other lInux box?

Thanks for any help in advance!

---

### Post by rjr162 on 2016-08-08
So far I'm stuck in the same boat. I haven't tried too hard yet, but using the flash provided by "adobe-flashplugin" or "flashplugin-installer" ends up at the same login cycle. I used FireFox as the Flash built into Chrome just sits at a spinning circle and never even loads the flash part (same with Chromium even with either one of the Ubuntu repo flash packages installed).

---

### Post by mc4man on 2016-08-08
I'd think the only chance would be with google-chrome. Here g-c fails on the provider login (unknown error) but if either of you can get past the provider login with g-c & it doesn't work then likely no way
(for FF here installed the libflash-hal plugin but no go, I think flash needs to be 19.x or higher.

Linux is totally deficient as far as live media content & if Canonical can't get the major providers to do apps then it's "convergence" is probably doomed

---

### Post by Bucky Ball on 2016-08-08
Would be helpful if you provided a link to the site you're trying to stream from. ;)

---

### Post by howefield on 2016-08-08
> **Bucky Ball said:**
> Would be helpful if you provided a link to the site you're trying to stream from. ;)

Isn't it in the thread title.. nbcolympics.com

---

### Post by Bucky Ball on 2016-08-08
> **howefield said:**
> Isn't it in the thread title.. nbcolympics.com

Doh! Apologies and thanks. My brain is scrambled from watching too much olympics. From the top of their FAQ.

> Q: What do I need to watch video on NBCOlympics.com?
A: In order to watch any video on NBCOlympics.com, you must install the latest version of Adobe(R) Flash(R) (supports v10 and above).

By the looks of this Flash 10 is fine and Firefox finished at 11.2 so things should work out-of-the-box. :-k
 
Considering the stream needs Flash 10 and you should have 11.2 it must be a problem it is probably related to something else. Not sure if adding other things will help or hinder as it appears they shouldn't be required. The problem seems to be with authentication.

Do you have ubuntu-restricted-extras installed? That will install flash 11.2 automatically and then, according to the NBCOlympic FAQ, it should work.

---

### Post by findlj52 on 2016-08-08
Yes, I have the newest version of ubuntu-restricted-extras.   I received that message when I tried to install it.  
I get the same result whether I try to stream from nbcolympics in either Firefox or Chrome.

> **Bucky Ball said:**
> Doh! Apologies and thanks. My brain is scrambled from watching too much olympics. From the top of their FAQ.



By the looks of this Flash 10 is fine and Firefox finished at 11.2 so things should work out-of-the-box. :-k
 
Considering the stream needs Flash 10 and you should have 11.2 it must be a problem it is probably related to something else. Not sure if adding other things will help or hinder as it appears they shouldn't be required. The problem seems to be with authentication.

Do you have ubuntu-restricted-extras installed? That will install flash 11.2 automatically and then, according to the NBCOlympic FAQ, it should work.

---

### Post by SeijiSensei on 2016-08-08
I'm watching [http://stream.nbcolympics.com/tennis-day-3-centre-court-day-session-match-1](http://stream.nbcolympics.com/tennis-day-3-centre-court-day-session-match-1) right now.

However, I use [pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") to run the Windows version of Flash player rather than the outdated version for Linux.  I also didn't get asked about my cable provider which I found surprising.

---

### Post by Bucky Ball on 2016-08-08
Are you getting to the screen shot I have attached and when you hit 'Sign in' it is taking you to a list of providers to choose from, you're choosing yours and the next step is asking you to log in to your provider?

SeijiSensei, so you are not getting any of the above? 

Another thing from their website; requirements for a browser are 

    Internet Explorer 11 (32 or 64-bit) and up
    Firefox 3.6
    Safari 5
    Chrome 16

According to their website, this looks like it is designed to be capable of running on some fairly dated hardware/software.

---

### Post by mc4man on 2016-08-08
Regular nbc/oly videos play ok with the older flash but the message here is that the live streams require 19+. Sort of a moot point as it won't work anyway in linux. 
The pipelight method is the way to go or use windows, mac, iOS, android, i.e. anything but linux.  For in browser adblockers shouldn't be running

Got pipelight working here & the live streams play fine (in USA) & didn't have to login though do see a line about logging in will provide full access?
(- so logged in no problem. I believe you only need to login once, at least with Firefox

---

### Post by findlj52 on 2016-08-09
After running...
sudo add-apt-repository ppa:pipelight/stable
(Note: for some reason this forum insists on changing 'colon p ' to the smiley emoticon!)

I receive these errors.

gpg: keyring `/tmp/tmpsq58u4tc/secring.gpg' created
gpg: keyring `/tmp/tmpsq58u4tc/pubring.gpg' created
gpg: requesting key 25396B8E from hkp server keyserver.ubuntu.com
gpgkeys: key 37D519856DA17931CD1123FBFB5DF26925396B8E can't be retrieved
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

Not sure where to go with this..

> **SeijiSensei said:**
> I'm watching [http://stream.nbcolympics.com/tennis-day-3-centre-court-day-session-match-1](http://stream.nbcolympics.com/tennis-day-3-centre-court-day-session-match-1) right now.

However, I use [pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") to run the Windows version of Flash player rather than the outdated version for Linux.  I also didn't get asked about my cable provider which I found surprising.

---

### Post by mc4man on 2016-08-09
Here did this way
Ran these 5 commands with Firefox closed
```
sudo add-apt-repository ppa:pipelight/stable
```
```
sudo apt-get update
```
```
sudo apt-get install --install-recommends pipelight-multi
```
```
sudo pipelight-plugin --update
```
```
sudo pipelight-plugin --enable flash
```
Then opened Firefox, let pipelight do it's thing.
After done closed Firefox & 1 final command
```
sudo pipelight-plugin --create-mozilla-plugins
```

Then for the moment activated the flash plugin to always as in screen

(- here logging in was best choice, only needed to do once then FF will do automatically

---

### Post by mc4man on 2016-08-09
as in (forum refused screen before

---

### Post by Keith_Helms on 2016-08-10
This appears to have pulled in a good part of wine. :)

After the install I now show 2 versions of Shockwave Flash under plugins - 11.2 r202 and 22.0 r0.  Does that matter?  I was able to stream a couple of the olympics segments from the nbc site so whichever one it is using is working.

---

### Post by SeijiSensei on 2016-08-10
Just disable or remove the Linux version of Flash via Tools > Add-ons > Plugins.  I only have Windows Flash via pipelight in my list of plugins.

---

### Post by findlj52 on 2016-08-14
Mc4man, The following set of commands worked perfectly for me.  Thank you very much.

Do note that I received the following errors when I issued the following command during the spotlight install...

   jim@Double-Naught-Linux:~$ sudo pipelight-plugin --update
 --2016-08-14 07:13:01--  [https://bitbucket.org/mmueller2012/pipelight/raw/master/share/install-dependency-1434FC73.sig](https://bitbucket.org/mmueller2012/pipelight/raw/master/share/install-dependency-1434FC73.sig)
 Resolving bitbucket.org (bitbucket.org)... 

 Connecting to bitbucket.org (bitbucket.org)|... connected.

 HTTP request sent, awaiting response... 200 OK
 Length: 29486 (29K) [text/plain]
 Saving to: ‘/tmp/tmp.L5vF3C3AhV’
 

 100%[=====================================>] 29,486      --.-K/s   in 0.01s    
 

 2016-08-14 07:13:02 (2.07 MB/s) - ‘/tmp/tmp.L5vF3C3AhV’ saved [29486/29486]
 

 gpg: WARNING: unsafe ownership on configuration file `/home/jim/.gnupg/gpg.conf'
 gpg: Signature made Sun 31 Jul 2016 01:12:05 PM CDT using RSA key ID 1434FC73
 gpg: Good signature from "Pipelight Dev Team (install-dependency) <webmaster@fds-team.de>"
 gpg: WARNING: This key is not certified with a trusted signature!
 gpg:          There is no indication that the signature belongs to the owner.
 Primary key fingerprint: CF23 08D4 3507 9A77 124E  01A2 83C7 3FB2 1434 FC73
 

 Script dependency-installer has been updated to version caf58d2cae5c4e5a6b902fa7b8fc5abbdb3d765fc7a518f70833a71ceaa42fbc




> **mc4man said:**
> Here did this way
Ran these 5 commands with Firefox closed
```
sudo add-apt-repository ppa:pipelight/stable
```
```
sudo apt-get update
```
```
sudo apt-get install --install-recommends pipelight-multi
```
```
sudo pipelight-plugin --update
```
```
sudo pipelight-plugin --enable flash
```
Then opened Firefox, let pipelight do it's thing.
After done closed Firefox & 1 final command
```
sudo pipelight-plugin --create-mozilla-plugins
```

Then for the moment activated the flash plugin to always as in screen

(- here logging in was best choice, only needed to do once then FF will do automatically

---

### Post by mc4man on 2016-08-14
> **findlj52 said:**
> 
Do note that I received the following errors when I issued the following command during the spotlight install...

 gpg: WARNING: unsafe ownership on configuration file `/home/jim/.gnupg/gpg.conf'
 
It's just a warning & in this instance can be ignored, see [here]("https://ubuntuforums.org/showthread.php?t=1448524") if inclined

---

