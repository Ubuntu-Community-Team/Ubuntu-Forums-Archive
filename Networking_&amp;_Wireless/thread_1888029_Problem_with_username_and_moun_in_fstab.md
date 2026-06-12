---
title: "Problem with username and moun in fstab"
date: 2011-11-28
forum: Networking &amp; Wireless
---

### Post by Leo Reijnen on 2011-11-28
Hi all,
 

 I have problem with mounts in fstab since I've upgraded to Ubuntu 11.10

 

 A line like:
 

 **//192.168.1.65/Documenten /mnt/docsleo cifs iocharset=utf8,file_mode=0777,dir_mode=0777,credentials=/home/leo/mountcredleo,uid=1000**
 

 used to work fine, with the mountcredleo file containing:
 **user=leo**
 **password=<password>**
 

 Now I get: mount error 13 permission denied
 

 Problem is, when upgrading to Ubuntu 10.10 I gave my full name, including a space, as username.
 

 How do I solve this? I see two options:
 
[LIST=1]
[*]Change the username in 	mountcredleo, but how do I make it accept the space in the name?
I 	have tried 'escaping' it wth a '\' and putting it in single or 	double quotes, but nothing works. And/or should I add this user to 	any groups? I tried, but I get the error: user 'Leo Reijnen' does no 	exist. Well, excuse me for breathing...
[*]Make a second admin account for 	user 'leo' with a temporary name – alias 'leo' is forbidden - 	delete the user 'Leo Reijnen' and then edit the new leo back to 	'leo'.  	
[/LIST]
 

 Of course there may be a simpler solution....
 Your input is highly appreciated.
 

 Leo Reijnen

---

### Post by Morbius1 on 2011-11-28
Spaces in Linux always confuse me because there are different ways to handle it that work only in different circumstances. 

You might try one of the following in place of a space:
```
\040
``````
%20
```I'll look through my notes to see if I've done this before in a credentials file.

---

### Post by Leo Reijnen on 2011-11-28
> **Morbius1 said:**
> Spaces in Linux always confuse me because there are different ways to handle it that work only in different circumstances. 

You might try one of the following in place of a space:
```
\040
``````
%20
```I'll look through my notes to see if I've done this before in a credentials file.
Thanks, Mobius1, but nope, both don't work in credentials nor with usermod...

---

### Post by Leo Reijnen on 2011-11-28
I now get the feeling the problem is elsewhere, because at bootup I get messages saying "network unreachable" and "waiting for network configuration" + "waiting 60 more seconds..." before it boots "without full network configuration". I have tried the steps outlined in [http://uksysadmin.wordpress.com/2011/10/14/upgrade-to-ubuntu-11-10-problem-waiting-for-network-configuration-then-black-screen-solution/](http://uksysadmin.wordpress.com/2011/10/14/upgrade-to-ubuntu-11-10-problem-waiting-for-network-configuration-then-black-screen-solution/)
but that didn't solve anything, and I didn't get the black screen, anyway.
The weird thing is that I have Internet access via wlan and I can succesfully ping the machine from which fstab is supposed to mount the shares.
Nothing has changed in my network set-up, so it must be some minor thing that I'm overlooking...

---

### Post by Leo Reijnen on 2011-11-28
It gets weirder. If I issue the command 'sudo mount -a' I still get "permission denied". The shares   do not show up on my desktop either. However, when I open LibreOffice Writer or Calc I can access the supposedly "not-mounted" shares and open documents to my heart's desire. As this is basically what I want, I'm happy, but still baffled... I will therefore not mark this thread "solved" and hope someone can shed some light on this.

---

### Post by Leo Reijnen on 2011-11-28
I now think that the issue is related to the fact that Ubuntu is waiting for the eth0 to come up, but since I dont have a wired connection, only wlan, it of course never finds it. I have tried many things to disable eth0, but to no avail. I keep getting the "waiting for network configuration" and "60 sends more" delay on booting.

---

