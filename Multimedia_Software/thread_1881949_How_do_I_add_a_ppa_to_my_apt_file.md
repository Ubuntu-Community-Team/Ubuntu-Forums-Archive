---
title: "How do I add a ppa to my apt file?"
date: 2011-11-16
forum: Multimedia Software
---

### Post by mpb1964 on 2011-11-16
I'm new here - so I hope I'm posting this properly. I want to install Handbrake on my 8.04 Ubuntu. I found a couple threads that mentioned a command called "add-apt-repository."
Code:
   sudo add-apt-repository ppa:stebbins/handbrake-snapshots
then Code:
   sudo apt-get update
then Code:
   sudo apt-get install handbrake-gtk ffmpeg

That command comes out in a later Ubuntu. What would I have to do to enter this myself?
I'm a newbie. I found a page on the forums that mentions the /etc/apt/sources.list file
but am not sure exactly how the line should look.
Any help would be appreciated.

---

### Post by snowpine on 2011-11-16
Welcome to the forums!
Sorry to say that 8.04 has reached its "end of life" and is no longer supported (unless you are running a server). This means no security updates or bug fixes, and it is not a beginner's task to install new software on an unsupported system.

Your Handbrake tutorial should work fine if you install a supported Ubuntu release, 10.04 or newer, available from [http://ubuntu.com](http://ubuntu.com)

---

### Post by wolfen69 on 2011-11-16
Just do
```
gksudo gedit /etc/apt/sources.list
```
and you will get a text editor with all the sources listed. You would then add a new line with the ppa address. Save and close.

---

### Post by matt_symes on 2011-11-16
Hi

> **mpb1964 said:**
> I'm new here - so I hope I'm posting this properly. I want to install Handbrake on my 8.04 Ubuntu. I found a couple threads that mentioned a command called "add-apt-repository."
Code:
   sudo add-apt-repository ppa:stebbins/handbrake-snapshots
then Code:
   sudo apt-get update
then Code:
   sudo apt-get install handbrake-gtk ffmpeg

That command comes out in a later Ubuntu. What would I have to do to enter this myself?

You open a terminal and type those three commands in one after another hitting the <enter> key after each.  You will have to enter your password. It will not be echoed to the  screen. This is normal.

> 
I'm a newbie. I found a page on the forums that mentions the /etc/apt/sources.list file
but am not sure exactly how the line should look.
Any help would be appreciated.PPA's are mostly kept in files in the directory /etc/apt/sources.list.d/ and are not kept in the main file /etc/apt/sources.list.

Here is a snip of mine.

```
matthew@matthew-laptop:~$ ls /etc/apt/sources.list.d/
dropbox.list.old                            
nilarimogard-webupd8-lucid.list      
psyke83-ppa-lucid.list               
stebbins-handbrake-snapshots-lucid.list       
webupd8team-jupiter-lucid.list                      
```As you can see, i also use the handbrake PPA.

Using add-apt-repository will create the PPA file for you and download the GPG keys as well.

EDIT:  *8.04 Ubuntu.* Somehow i saw this as 10.04 ! Snowpine is right. Upgrade !

Kind regards

---

### Post by mpb1964 on 2011-11-16
Thanks for the relpies! I know - I need to upgrade ( did a post on recommended places to buy CD's) Any ideas there - would prefer to get Cd rather than do ISOs.
Anyway, Thanks to everyone for the replies. :D

---

