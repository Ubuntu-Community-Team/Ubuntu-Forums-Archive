---
title: "Updates and Package Installer Problem"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by cloudsymph on 2009-11-15
hey there everyone.  earlier i've posted a thread on my wired internet not working, which from help i have resolved it, as it seemed to have been a problem with the ipv6.  the following thread:

```
http://ubuntuforums.org/showthread.php?p=8262760#post8262760
```

now there is something else i have a problem with.  as the title states it's to do with updating and the package installer.  the problem is, though i can use the internet for browsing and such now, i can't install anything nor can i update.  

in the thread above i said that when i was in the package installer, when i click on something i want to install, there is no "install" or "uninstall" button, and after a bit of playing around i managed to get those two buttons.  however the installation when i decide to install would not continue nor would i be able to download the specific program.  

this is the same with the updates.  the OS picks up what i need to install but i am unable to download and install the files.

also this is the message i'm getting with trying to install compizconfig-settings-manager and adobe-flash.  adobe was downloaded from the adobe website, but it seems that there was still a need to download packages after getting the flash file from their website.

```
requires installation of untrusted packages
the action would require the installation of packages from not authenticated sources.

>details
compizconfig-settings-manager python-compizconfig
```

with adobe flash

```
requires installation of untrusted packages
the action would require the installation of packages from not authenticated sources.

>details
flashplugin-installer
```

so yeah, if anyone could shed some light on this that would be great.  also i've currently got win7 installed on the laptop that i want to use ubuntu on (dell inspiron 640 m), so posting back results from the command line may take a while (as i will reinstall ubuntu 9.10).

and one last thing.  if there is any commands you would like me to type in the terminal, please write me the full set of commands to type, i'm a terminal noob you see =D.

oh yes and thanks in advance.

---

### Post by madScientist3 on 2009-11-19
I have the same problem and got no reply to my post. I disabled my ipv6 (because my router does not support it) and my internet, skype and network are fine. However I cannot update. I can do an occasional apt-get update but I have to go to software sources, choose other, select the best option then do the apt-get immediately. But update manager will not connect to do updates. I have tried wired as well as wireless with same results, as well as connecting at work.
I am stuck as to a solution.

---

### Post by johnofwax on 2010-02-24
Posting to help others:
I just received the same error message. I used apt-get on the command line to install what i needed, but I didnt want to have to revert to that all the time. I like browsing the software manager for games and stuff. So after installing 2 packages on the command line, I went searching for the issue.
My steps were:
System>Administration>Software Sources
I had "Proprietary Drivers" and "Software Restricted by copyright or legal issues" checked.
I unchecked the two of these. I then went to the Authentication tab. I clicked "restore defaults", although nothing changed.
I closed the window, and tried the Software manager again.
Worked like a charm. Don't know how the settings were changed in the first place, but whatever. Hope it helps somebody browsing, since at this moment, this is google's #1 result for the error message.

---

### Post by lazymangaka on 2010-05-09
I had the same problem, and those steps--for whatever reason--worked perfectly. I was attempting to install K9Copy and received the same error message.

---

### Post by videomusik on 2010-06-01
I just had the same problem today, and the steps in the above post worked like a charm. Thanks.

---

### Post by PC_Genius on 2010-06-01
I am also having this problem. I'm quite frustrated at this. My story is:

Basically this morning I started up my laptop and went on facebook, I found a new notification and it was my friend writting to me (to cut the story short), I replied back to him but forgot to click "Send message". Left my laptop for about 10 minutes, Came back, logged back on (Since it went on screen saver) and and my keyboard suddenly wouldnt write anything.  I didn't experiment on this since I thought a restart of the computer would solve this problem. I restarted my computer and my keyboard started working again. Little did I know that other things stopped working, like for starters my Wireless driver suddenly disappeared from my Network icon, only the "Wired connection" was displayed. Then my sound driver was unistalled. I looked into it and it seems my computer had updated without me knowing and this update had unistalled my wireless broadcom driver and sound. I plugged in my laptop to the ethernet (Since thats the only way I could get on my router) And tried to download several wireless programs from ubuntu software centre, and I am getting the same message that other people on this thread have been getting. 


My post may have to be moved to another thread. But I would like a suggestion to either my Wireless problem/Sound problem Or my Ubuntu Software Centre error. The error is "Requires installation of untrusted packages. The action would require the installation of packages from not authenticated sources."


Any help would be appreciated. Thanks!

---

### Post by PC_Genius on 2010-06-01
I tried what Johnofwax posted and like others, it worked like a charm! Thanks! I'll keep you updated on my wireless problem/sound problem. Thanks!

---

### Post by V.V.V. on 2010-06-09
I've had the same problem when tried to install the restricted extras. As for me it worked ok just to open the "Software Sources" window, uncheck the "Software restricted by copyright or legal issues (multiverse)", close the window saving settings, open the "Software Sources" window again, check the checkbox back and close the window. Thanks, johnofwax!

---

### Post by Jakiejake on 2010-06-24
> **johnofwax said:**
> Posting to help others:
I just received the same error message. I used apt-get on the command line to install what i needed, but I didnt want to have to revert to that all the time. I like browsing the software manager for games and stuff. So after installing 2 packages on the command line, I went searching for the issue.
My steps were:
System>Administration>Software Sources
I had "Proprietary Drivers" and "Software Restricted by copyright or legal issues" checked.
I unchecked the two of these. I then went to the Authentication tab. I clicked "restore defaults", although nothing changed.
I closed the window, and tried the Software manager again.
Worked like a charm. Don't know how the settings were changed in the first place, but whatever. Hope it helps somebody browsing, since at this moment, this is google's #1 result for the error message.

Worked!

---

### Post by stuhpa on 2010-06-25
> **johnofwax said:**
> Posting to help others:
I just received the same error message. I used apt-get on the command line to install what i needed, but I didnt want to have to revert to that all the time. I like browsing the software manager for games and stuff. So after installing 2 packages on the command line, I went searching for the issue.
My steps were:
System>Administration>Software Sources
I had "Proprietary Drivers" and "Software Restricted by copyright or legal issues" checked.
I unchecked the two of these. I then went to the Authentication tab. I clicked "restore defaults", although nothing changed.
I closed the window, and tried the Software manager again.
Worked like a charm. Don't know how the settings were changed in the first place, but whatever. Hope it helps somebody browsing, since at this moment, this is google's #1 result for the error message.

Works like a charm
Ty

---

### Post by ArionKrause on 2010-08-08
Worked for me as well!

---

### Post by torgis on 2010-09-21
worked for me as well.  thanks mate!

---

### Post by coolman98 on 2010-10-01
works great but I still kinda need multiverdse

---

### Post by agreenbhm on 2010-10-01
> **coolman98 said:**
> works great but I still kinda need multiverdse

Re-check the options when you're done.

---

### Post by apiccirilli on 2010-10-08
> **johnofwax said:**
> Posting to help others:
I just received the same error message. I used apt-get on the command line to install what i needed, but I didnt want to have to revert to that all the time. I like browsing the software manager for games and stuff. So after installing 2 packages on the command line, I went searching for the issue.
My steps were:
System>Administration>Software Sources
I had "Proprietary Drivers" and "Software Restricted by copyright or legal issues" checked.
I unchecked the two of these. I then went to the Authentication tab. I clicked "restore defaults", although nothing changed.
I closed the window, and tried the Software manager again.
Worked like a charm. Don't know how the settings were changed in the first place, but whatever. Hope it helps somebody browsing, since at this moment, this is google's #1 result for the error message.

Same problem, and this worked like a charm for me - and I also checked the Proprietary Drivers & Software Restricted... back to how they were.  Odd bug!

---

### Post by patC42 on 2010-10-08
Still works cheers and thanx

---

### Post by vegasmartn on 2010-10-25
Hi, 
I am getting those errors a lot while using software manager. Solution provided in this post didn't work for me while trying to get audacity.

I am having more luck with actual terminal rather than software center.

Command that worked:

sudo apt-get install audacity

---

### Post by yanike on 2010-10-26
> **johnofwax said:**
> Posting to help others:
I just received the same error message. I used apt-get on the command line to install what i needed, but I didnt want to have to revert to that all the time. I like browsing the software manager for games and stuff. So after installing 2 packages on the command line, I went searching for the issue.
My steps were:
System>Administration>Software Sources
I had "Proprietary Drivers" and "Software Restricted by copyright or legal issues" checked.
I unchecked the two of these. I then went to the Authentication tab. I clicked "restore defaults", although nothing changed.
I closed the window, and tried the Software manager again.
Worked like a charm. Don't know how the settings were changed in the first place, but whatever. Hope it helps somebody browsing, since at this moment, this is google's #1 result for the error message.

Thanks johnofwax!

Also, I found if you change the download server to "Main Server" it will help as well. If it's already on "Main Server", change it to something else and back to "Main Server" and things will install (including audacity and others).

[IMG]http://img4.imageshack.us/img4/1325/screenshotpu.png[/IMG]

P.S. The theme in the screenshot is my [YeoWorks Theme]("http://www.winmatrix.com/forums/index.php?/topic/29798-yeoworks-os-theme-for-ubuntu/") I'm creating right now that will be released later :)

---

### Post by gotalot2do on 2010-11-09
I have been having the same problem with a lot of installs. I have just removed my aptitude package manager and things seem to install now, not sure if this will be the same for the rest of you but thought I would let you know what works for me.

---

### Post by M.Saber on 2010-11-18
worked for me 
ty

---

### Post by nareshpathi on 2010-11-19
Thanks. Those steps worked for me.

---

### Post by JDHS on 2010-11-27
I'm glad to find this fix here. I'm pretty sure that the problem results from using the "Install proprietary drivers" action (e.g. for nvidia cards or whatever) when setting up a new system.

---

### Post by ben2talk on 2011-01-11
> **johnofwax said:**
> Posting to help others:
I just received the same error message. I used apt-get on the command line to install what i needed, but I didnt want to have to revert to that all the time. I like browsing the software manager for games and stuff. So after installing 2 packages on the command line, I went searching for the issue.
My steps were:
System>Administration>Software Sources
I had "Proprietary Drivers" and "Software Restricted by copyright or legal issues" checked.
I unchecked the two of these. I then went to the Authentication tab. I clicked "restore defaults", although nothing changed.
I closed the window, and tried the Software manager again.
Worked like a charm. Don't know how the settings were changed in the first place, but whatever. Hope it helps somebody browsing, since at this moment, this is google's #1 result for the error message.

Sure it works - basically you're just turning off drivers (like nVidia or ATI drivers) as well as Multiverse (mp3, and other important codecs which are not as Free as they should be and cannot therefore be included as standard in a Free desktop).

After doing this, you should update and then return and re-enable them.

For a single package (for me, Shotwell today) it's easier to use terminal. I'm not sure how it's difficult - assuming people make things easy for themselves.

I'm personally very lazy, so I set up Keyboard Shortcuts for myself. Pressing Super + T opens my terminal and I have edited my .bashrc to include a line for installing:
```
alias install='sudo aptitude install'
```

I also have 'apt-fast' which can be good on bigger installs, so I have also 
```
alias finstall='sudo apt-fast install'
```

so my solution is to press Super + T to get a terminal, then type ```
finstall shotwell
```

to take a look at your .bashrc, you can simply do ALT +F2 and type '```
gedit .bashrc
```'.

This issue only applies to Update Manager, when you install with Aptitude it warns and prompts you to interact Yes or No to continue... so I would rate this as a bug.

---

### Post by Tirean on 2011-01-12
> **johnofwax said:**
> Posting to help others:
I just received the same error message. I used apt-get on the command line to install what i needed, but I didnt want to have to revert to that all the time. I like browsing the software manager for games and stuff. So after installing 2 packages on the command line, I went searching for the issue.
My steps were:
System>Administration>Software Sources
I had "Proprietary Drivers" and "Software Restricted by copyright or legal issues" checked.
I unchecked the two of these. I then went to the Authentication tab. I clicked "restore defaults", although nothing changed.
I closed the window, and tried the Software manager again.
Worked like a charm. Don't know how the settings were changed in the first place, but whatever. Hope it helps somebody browsing, since at this moment, this is google's #1 result for the error message.

Yeah, This most definitely solved the issue for me too. Thanks for posting it!

---

### Post by nutsy.ben on 2011-02-08
> **johnofwax said:**
> Posting to help others:
I just received the same error message. I used apt-get on the command line to install what i needed, but I didnt want to have to revert to that all the time. I like browsing the software manager for games and stuff. So after installing 2 packages on the command line, I went searching for the issue.
My steps were:
System>Administration>Software Sources
I had "Proprietary Drivers" and "Software Restricted by copyright or legal issues" checked.
I unchecked the two of these. I then went to the Authentication tab. I clicked "restore defaults", although nothing changed.
I closed the window, and tried the Software manager again.
Worked like a charm. Don't know how the settings were changed in the first place, but whatever. Hope it helps somebody browsing, since at this moment, this is google's #1 result for the error message.

Software sources is now in Ubuntu Software Center or in the settings of the update manager

---

### Post by ae75rhenium on 2011-02-13
This also worked for me. Thanks. Whenever I have a problem I always come here and my problems are no more.

---

### Post by FML on 2011-02-20
It works fine, but why?

---

### Post by rva1945 on 2011-03-26
> **johnofwax said:**
> Posting to help others:
I just received the same error message. I used apt-get on the command line to install what i needed, but I didnt want to have to revert to that all the time. I like browsing the software manager for games and stuff. So after installing 2 packages on the command line, I went searching for the issue.
My steps were:
System>Administration>Software Sources
I had "Proprietary Drivers" and "Software Restricted by copyright or legal issues" checked.
I unchecked the two of these. I then went to the Authentication tab. I clicked "restore defaults", although nothing changed.
I closed the window, and tried the Software manager again.
Worked like a charm. Don't know how the settings were changed in the first place, but whatever. Hope it helps somebody browsing, since at this moment, this is google's #1 result for the error message.

I'm having the same problem. I have Maverick and can't find System-Administration-Software Sources.

---

### Post by deathbydoubleG on 2011-04-06
it worked :lolflag:

i think it just had to clear and update the cache. (I THINK) 

:guitar::popcorn:

---

### Post by DaLexisX on 2011-04-23
> **rva1945 said:**
> I'm having the same problem. I have Maverick and can't find System-Administration-Software Sources.


Quoted from PsychoCats.net:

To get to the sources, you'll have to go to System > Administration  > Synaptic Package Manager and then Settings > Repositories.

HTH

---

### Post by Pilot824 on 2011-06-08
I was getting generally the same problem, except it was trying to repair a few things. So far its repairing, thanks John!

> **johnofwax said:**
> Posting to help others:
I just received the same error message. I used apt-get on the command line to install what i needed, but I didnt want to have to revert to that all the time. I like browsing the software manager for games and stuff. So after installing 2 packages on the command line, I went searching for the issue.
My steps were:
System>Administration>Software Sources
I had "Proprietary Drivers" and "Software Restricted by copyright or legal issues" checked.
I unchecked the two of these. I then went to the Authentication tab. I clicked "restore defaults", although nothing changed.
I closed the window, and tried the Software manager again.
Worked like a charm. Don't know how the settings were changed in the first place, but whatever. Hope it helps somebody browsing, since at this moment, this is google's #1 result for the error message.

---

### Post by waynerod on 2011-06-29
> **johnofwax said:**
> Posting to help others:
I just received the same error message. I used apt-get on the command line to install what i needed, but I didnt want to have to revert to that all the time. I like browsing the software manager for games and stuff. So after installing 2 packages on the command line, I went searching for the issue.
My steps were:
System>Administration>Software Sources
I had "Proprietary Drivers" and "Software Restricted by copyright or legal issues" checked.
I unchecked the two of these. I then went to the Authentication tab. I clicked "restore defaults", although nothing changed.
I closed the window, and tried the Software manager again.
Worked like a charm. Don't know how the settings were changed in the first place, but whatever. Hope it helps somebody browsing, since at this moment, this is google's #1 result for the error message.

Sadly, this didn't work for me. :(
P.S. I'm running Ubuntu 11.04. (So maybe there's something changed?)

---

### Post by nm_geo on 2011-06-29
Open terminal 

```
sudo apt-get update
```

then if you want to get needed upgrades

```
sudo apt-get upgrades
```

---

### Post by PouncingAnt on 2011-07-08
> **nm_geo said:**
> Open terminal 

```
sudo apt-get update
```

then if you want to get needed upgrades

```
sudo apt-get upgrades
```

I find this the best answer as it lets me retain my untrusted sources. Good work!

[SIZE="1"]NB: I should point out I had to remove the s at the end of "apt-get upgrades" to get it to work on ubuntu-11.04[/SIZE]

---

### Post by lemaza on 2011-07-29
I am using ubuntu 11.04 and I have the same problem using the update manager and ubuntu software center .. i have tried all the solutions but nothing worked , and i don't want to use the terminal as I have no idea in dealing with it .. can anybody help ?

---

### Post by Onruli Jr. on 2011-08-07
Hi, i tried the way johnofwax had suggested but it did not work for me, still it shows  
requires installation of untrusted packages
the action would require the installation of packages from not authenticated sources.
pls help me :confused::(

---

### Post by pakkatechie on 2011-08-08
i had the same issue when i was using update-manger for regular updates. I got the error when i tried update. 

When i issued "sudo apt-get update" and "sudo apt-get upgrade". Everything went fine. :-D

---

### Post by nerderello on 2011-10-17
similar problem getting latest Wine upgrade (after upgrading to 11.10 of Ubuntu). Had to re-add the repository (as per Wine's site).

When I tried to "sudo apt-get update" I received (after a load of other stuff):
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

So I did:
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0
(where the hex number is a cut and paste from the error message).

This gave this:
> ntu.com --recv-keys 5A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

And then doing a 
> sudo apt-get update

And allowed me to do the usual updates.

---

### Post by spamless on 2011-10-23
> **nerderello said:**
> similar problem getting latest Wine upgrade (after upgrading to 11.10 of Ubuntu). Had to re-add the repository (as per Wine's site).

This was exactly my issue, and with the same binary key as the problem. This one is appreciated.

---

### Post by kyral210 on 2011-11-07
I am having this problem now (over a year after the original post, but the solution proposed doesn't work! Is there anything else I can do?

---

### Post by s.m.knipe on 2011-12-28
bump

The Terminal commands are fine, but it would be nice if the GUI package manager could be fixed to respond properly to the keys

---

### Post by negahesard on 2012-03-26
Thanks alot .. 
your job helped me very much..

---

