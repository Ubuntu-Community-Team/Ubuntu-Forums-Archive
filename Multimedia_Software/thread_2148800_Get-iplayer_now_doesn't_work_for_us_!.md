---
title: "Get-iplayer now doesn't work for us !"
date: 2013-05-26
forum: Multimedia Software
---

### Post by grey1beard on 2013-05-26
My wife regularly downloads video and radio programmes from the BBC via get-iplayer using 12.04 on a Sony viao, but this morning half way through a download it came up with an error message.
To check, I tried the same down load on my hp6700, and the first programme downloaded OK, but the second one threw up the same error message  ......

> WARNING: ffmpeg does not exist - not converting flv file
INFO: File name prefix = Sherlock_Series_1_-_2._The_Blind_Banker_b00tc6t2_default                 
WARNING: Your version of flvstreamer/rtmpdump does not support SWF Verification
FLVStreamer v2.1c1
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
ERROR: Last tag size must be greater/equal zero (prevTagSize=400147357) and smaller then filesize, corrupt file!
INFO: Command exit code 1 (raw code = 256)
WARNING: Retry recording for 'Sherlock: Series 1 - 2. The Blind Banker (b00tc6t2)'

Her laptop downloads radio programmes via get-iplayer OK, but not videos.

We'd be very grateful if anyone could advise, and guide us towards solving the problem.

John

---

### Post by grey1beard on 2013-05-26
OK, so my laptop doesn't like me telling tales out of school !
This time it worked as normal, with the usual error message that seems to be part of the workaround.
I've no idea why, as I havent done anything differently.
At both previous attempts, I removed the partial downloads, before trying again, as previous experience has shown that sometimes a restart will pick up where it left off, but sometimes not.

So at this moment, both laptops are behaving themselves, but if anyone can point out any hidden meaning in the error message, at least I'd have learned something !

John

---

### Post by grey1beard on 2013-05-27
This morning, the same thing has occurred, with the error message as before, the download reaching ~430 Mb out of a total ~560 Mb.
> ERROR: Last tag size must be greater/equal zero (prevTagSize=400147357) and smaller then filesize, corrupt file!
INFO: Command exit code 1 (raw code = 256)

She's removed the partial download, and is trying again.
I have a feeling that the problem is external to the laptop, but have no knowledge to back that up.

It's just failed again, at 288 Mb, with only the "prevTagSize" figure different.

Trying for a third time.:confused:

---

### Post by grey1beard on 2013-05-27
This time a new message has appeared, a window in front of the terminal window (which is showing a simillar message as before) -

> Problem in flvstreamer

Sorry, the program flvstreamer closed unexpectedly.
Your computer does not have enough free memory to automatically analyse the problem and send a report to the developers.

Possibly not significant, but then what do I know  :(

John

---

### Post by coldraven on 2013-05-27
> WARNING: ffmpeg does not exist - not converting flv file

See this thread:
[http://ubuntuforums.org/showthread.php?t=2146007&p=12651629#post12651629](http://ubuntuforums.org/showthread.php?t=2146007&p=12651629#post12651629)

I'm not sure about the other errors but it may help if you have the latest version of get_iplayer.
You have trimmed your output so I cannot see, it should be vers. 2.8.2
If not go here:
[http://www.infradead.org/get_iplayer/html/get_iplayer.html](http://www.infradead.org/get_iplayer/html/get_iplayer.html)
Download and extract the get_iplayer perl script (348.4kB) and just overwrite the version that you have in /usr/bin.
Edit: You will need to change the permissions to match the original file. 
Use "gksu nautilus" in a terminal
Set 
Owner = root (RW)
Group = root (R)
Others = Read Only
Execute = Allow 

To extract just double click the get_iplayer.tar.gz file.

---

### Post by speartip on 2013-05-27
get-iplayer is working fine here, but I updated get-iplayer & ffmpeg using the following commands:
```
sudo add-apt-repository ppa:jon-severinsson/ffmpeg
```
and
```
sudo add-apt-repository ppa:jon-hedgerows/get-iplayer
```
then
```
sudo apt-get update && sudo apt-get upgrade
```

Everything should now work fine.

---

### Post by grey1beard on 2013-05-27
Hi coldraven, and thanks for your help.
Both our laptops have 2.80 running on them, so I'll try setting mine up first.
I've downloaded 2.82 and extracted the contents as a folder get_iplayer-2.82 onto my desktop.

> **coldraven said:**
> 
Edit: You will need to change the permissions to match the original file. 
Use "gksu nautilus" in a terminal
Set 
Owner = root (RW)
Group = root (R)
Others = Read Only
Execute = Allow 

To extract just double click the get_iplayer.tar.gz file.

Sorry, coldraven, but this has got me lost. I've never used gksu nautilus before, so when I typed it into Terminal, gave it my password, I was then faced with a Terminal line -"Initialising nautilus-gdu extension " and a window showing my home folder. So my next step is unknown to me.

I understand what I am trying to do, but not the route !
So I'd be grateful if you could spell it out for me.
John

---

### Post by grey1beard on 2013-05-27
Hi speartip.
I used your lines of code on my wifes laptop, and so far all seems well.
However, something that has happened to me before has re-occurred. Update manager immediately ran and gave me a warning message over the top of the UM window, to the effect that some of the updates were unauthenticated. How do you get round this, as it keeps reappearing ? I tried just unticking the ppa entries which seemed to be the problem, but I'm thinking it will come back again in the future.
Regards
John

---

### Post by speartip on 2013-05-28
> **grey1beard said:**
> Hi speartip.
However, something that has happened to me before has re-occurred. Update manager immediately ran and gave me a warning message over the top of the UM window, to the effect that some of the updates were unauthenticated. How do you get round this, as it keeps reappearing ? I tried just unticking the ppa entries which seemed to be the problem, but I'm thinking it will come back again in the future.
Regards
John

Not too sure, the 2 ppas I gave above should not give that error.
A quick google brought this up, it may help.
[http://www.answeredubuntu.com/85641/how_do_i_deal_with_unauthenticated_sources_errors_in_the_software_center](http://www.answeredubuntu.com/85641/how_do_i_deal_with_unauthenticated_sources_errors_in_the_software_center)

---

### Post by grey1beard on 2013-05-28
Thanks speartip. 
Looks promising, and if the problem persists, I'll try that. 
I'm assuming that approach is universal ?

Regards
John

---

### Post by coldraven on 2013-05-28
> Sorry, coldraven, but this has got me lost. I've never used gksu  nautilus before, so when I typed it into Terminal, gave it my password, I  was then faced with a Terminal line -"Initialising nautilus-gdu  extension " and a window showing my home folder. So my next step is  unknown to me.


The command "gksu nautilus" runs the normal file browser but in "root" mode. That means you can edit files in the file system that are normally off limits to you as a user. Beware, you could break something if you edit or delete something critical.
It is probably better to use speartip's advice which will auto-update.

For your future information, if you had used nautilus and clicked on "File System" then "usr" then "bin" you would have found that the get_iplayer file lives in that folder. In geek speak you would have been in /usr/bin, where the leading forward slash means the root of the file system.
Tip: In /usr/bin are hundreds of files. To see get_player just start typing "get_" to jump to the the file. 

As an experiment go to any folder in the nautilus file browser and then press Ctrl+L. You will see that the location bar changes to show the path as mentioned above. You can actually copy and paste a location there, hit Enter and that's where you will go.
Note: pressing Ctrl+L again should toggle the location bar style but no longer works in Ubuntu 12.10

Hope all is working now.

---

### Post by grey1beard on 2013-05-28
Many thanks for the detailed instructions, coldraven. Its given me another tool to use.
Regards
John

---

### Post by grey1beard on 2013-06-01
i've now 'un-solved' this thread as the problem with Update manager had reappeared, and I now realise on careful inspection that my wife's laptop still has version 2.80 of get-ipayer, in spite of running speartips lines of code in Terminal.
I've just repated running sudo apt-get upgrade and got the result

> Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
   get-iplayer
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

So that's where I am at the moment :(

John

---

### Post by ron999 on 2013-06-01
> **grey1beard said:**
> ... I now realise on careful inspection that my wife's laptop still has version 2.80 of get-ipayer, in spite of running speartips lines of code in Terminal.

Try again...
_Add the repository_
```
sudo add-apt-repository ppa:jon-hedgerows/get-iplayer
```
_Update_
```
sudo apt-get update
```
_Install_
```
sudo apt-get -y install get-iplayer mplayer ffmpeg
```

---

### Post by dinkypumpkin on 2013-06-01
grey1beard: The PPA install described by ron999 is the best choice for upgrading an obsolete get-iplayer package on Ubuntu.  However, if you are of a more conservative bent there is another way to upgrade that doesn't entail any poking around in /usr/bin or using "gksu nautilus".  Because the get-iplayer package doesn't depend on specific versions of any of its dependencies, you can download the newer get-iplayer_2.82-2 package from the raring repo and install it in place of get-iplayer_2.80-1 that came with precise. get-iplayer_2.82-2 is the minimum version you should have to avoid any potential problems due to iPlayer changes after 2.80 was released.

1. Download get-iplayer_2.82-2 from raring repo.  Pick a mirror at:

[http://packages.ubuntu.com/raring/all/get-iplayer/download](http://packages.ubuntu.com/raring/all/get-iplayer/download)

2. Remove get-iplayer_2.80-1:

```
sudo dpkg -r get-player
```

3. Install  get-iplayer_2.82-2 from downloaded package:

```
sudo dpkg -i get-iplayer_2.82-2_all.deb
```

4. Ensure all suggested dependencies are installed (omit any already installed):

```
sudo apt-get install rtmpdump ffmpeg mplayer libmp3-tag-perl
```

5. Remove obsolete dependency (unnecessary with rtmpdump installed)

```
sudo apt-get remove flvstreamer
```

The end result is that you will have older (compared to PPA) versions of get-iplayer, rtmpdump and atomicparsley, but everything should still work OK.

---

### Post by speartip on 2013-06-02
John...
To upgrade iplayer try:
```
sudo apt-get dist-upgrade
```
That should work.

---

### Post by grey1beard on 2013-06-02
Thanks Guys. As soon as madam has gone out to the garden, and I can get my hands on her laptop, I'll have a go.  
;)

Regards all,
John

---

### Post by grey1beard on 2013-06-02
> **speartip said:**
> John...
To upgrade iplayer try:
```
sudo apt-get dist-upgrade
```
That should work.

It did. 
Many thanks speartip, so once again, fingers crossed, I can mark this thread solved !

Regards
John

---

### Post by ZaphodFJ on 2013-06-10
Magic - thanks!

(OK, not magic - there's no such thing- but you get the idea ;-)

---

### Post by grey1beard on 2013-06-10
Well, our delight was short lived.   :rolleyes:

I've attached two screen shots that I hope will sum up the problem now.
I've used both apt-get update and apt-get dist-upgrade when todays mess happened, but it hasn't resolved the issue.
Help gratefully received.

John

PS Radio programmes download OK, but not TV

---

### Post by speartip on 2013-06-11
The get-iplayer ppa was updated last night. It is now working properly,
For those who have applied the fix, I suggest you delete your .get_iplayer file in your home folder & start with a clean profile.
I have downloaded a program this morning with no problem.

---

### Post by grey1beard on 2013-06-11
Thanks speartip. Once again we're up and running !
John

---

### Post by dinkypumpkin on 2013-06-11
> **speartip said:**
> The get-iplayer ppa was updated last night. It is now working properly,
For those who have applied the fix, I suggest you delete your .get_iplayer file in your home folder & start with a clean profile.
I have downloaded a program this morning with no problem.


That is **very** bad advice.  $HOME/.get_iplayer is not a file, it is a directory.  It contains your user options file, your download history, programme caches, presets, and pvr searches.  There is absolute no reason to delete all that because of the latest changes to get_iplayer.  If you edited  /usr/bin/get_iplayer to insert the new SWF player URL, it will be replaced by upgrading from the PPA, so no problem.  If instead you changed your preferences as described in this thread:
[COLOR=#000000]
[/COLOR][http://ubuntuforums.org/showthread.php?t=2152221](http://ubuntuforums.org/showthread.php?t=2152221)[COLOR=#000000]
[/COLOR][COLOR=#000000]
then read this page:[/COLOR]

[https://github.com/dinkypumpkin/get_iplayer/wiki/swfurl](https://github.com/dinkypumpkin/get_iplayer/wiki/swfurl)

for instructions on reverting the changes.  The digested read:

Paste this to a command prompt and run -

```
get_iplayer --prefs-del --rtmp-tv-opts="--swfVfy=http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf" 
```

---

### Post by grey1beard on 2013-06-28
Hi dinkypumpkin,
I've just updated my laptop OK using your instructions, and it went flawlessly.
Problem with my wifes laptop (same Ubuntu version 12.04 LTS). 
It threw up the following error in the Terminal screen (see attached)
Any advice ?
Regards
John

---

### Post by dinkypumpkin on 2013-06-28
That is a rather esoteric bug in the add-apt-repository machinery that affects only some hardware.  I've never encountered it myself.  See:

[thread]2109324[/thread]

which suggests that downgrading the python-software-properties package is the solution:

[COLOR=#000000]```
sudo apt-get install python-software-properties=0.82.7
```

The related bug report: [/COLOR][lpbug]1063350[/lpbug]

---

### Post by grey1beard on 2013-06-29
[COLOR=#000000]```
sudo apt-get install python-software-properties=0.8.27
```

produced
 [B]E: Version '0.8.27' for 'python-software-properties' was not found
[/B]

I read the bug report, a lot of which I could understand, and saw the references to the variation in cpu type possibly being a common source of the bug.
Her laptop uses an AMD Athlon XP 1400+ (MME ? - certainly not SSE, as I remember when trying to sort out the problem of not being able to update Flash).

EDIT python version 2.7.3 installed. Do I also need to downgrade python to 2.7 ? Struggling out of my depth !

John

---

### Post by dinkypumpkin on 2013-06-29
Sorry, copy-and-paste failure:

```
sudo apt-get install python-software-properties=0.82.7
```

No need to downgrade Python - Python version not the issue.

---

### Post by grey1beard on 2013-06-29
All now OK.
Special thanks from SWMBO !

John

---

### Post by grey1beard on 2013-06-29
Yes, the get-iplayer now functions OK.
Unfortunately, the flash player problem has now re-appeared, and flately refuses to play anything on BBC or youtube !
I wonder if that's a coincidence ?

John

---

