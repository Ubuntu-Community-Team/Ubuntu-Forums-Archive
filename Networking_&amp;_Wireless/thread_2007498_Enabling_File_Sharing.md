---
title: "Enabling File Sharing"
date: 2012-06-20
forum: Networking &amp; Wireless
---

### Post by akaPrilly on 2012-06-20
Good afternoon one and all:

I am new to the Linux OS and today I  have been working diligently on being able to file share between my  desktop computer (which is running Ubuntu 12.04) and my older laptop,  which is running Windows XP Pro.    



Here is what I know that I have done so far:  

I installed Samba from the _Ubuntu Software Center,_ specifically:

[LIST]
[*]The Samba GUI for creating, modifying, and deleting Samba shares and users
[*]SMB/CIFS file, print, and login server for Unix
[/LIST]
 I  have tried following several on-line tutorials hoping to figure this  out but have not been successful in getting all of the way through the  steps.   Some of the guides written seem to be for older versions of  Ubuntu.  The last one that I tried following was based mostly on typing  in commands within Terminal:

 

 [http://comtech247.net/2012/05/04/how-to-configure-file-sharing-on-ubuntu-12-04-lts/](http://comtech247.net/2012/05/04/how-to-configure-file-sharing-on-ubuntu-12-04-lts/)
 

 Instructions seemed to go pretty much as outlined, until I typed in 
 [B][SIZE=2]gksu nano /etc/samba/smb.conf  [/SIZE]
[/B]
 and hit [Enter]  
Here is what came up next:

[SIZE=1]#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic
                               [ Read 341 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell[/SIZE]

[SIZE=2]It looks like Terminal is waiting for a response from me, but quite frankly, I don't know what to tell it or how to tell it.   [/SIZE]I  have tried everything that I thought off to continue forward.   I do  not even know if this tutorial would get me to my end objective.  Could  someone out there please help shed some light on what my next step(s)  should be?

Thanks in advance,

---

### Post by howefield on 2012-06-20
Use the key board shortcuts at the bottom of the terminal output to navigate around.

Or substitute nano with gedit to open up the text file for editing, might be easier for you to navigate around.

---

