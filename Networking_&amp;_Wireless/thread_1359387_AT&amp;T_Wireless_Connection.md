---
title: "AT&amp;T Wireless Connection"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by qkzoo on 2009-12-19
Hello,

I recently took an extra x86 PC I wasn't using and installed Ubuntu 9.10 on it.  This is my first experience with any Linux environment.  Here's the catch, on my Windows XP box, I can hook my Pocket PC up to it and get an internet connection using the Internet Sharing application on the phone.  It's pretty simple.  I was curious, because we have no other internet out here in the sticks, so I plugged via USB my Pocket PC into the Ubuntu box.  Ubuntu immediately picked up on the fact that there was a new internet connection.  I loaded Firefox and did a quick Google search and got results.  I then tried to load a few other web sites, including this one, and they just wouldn't load, they timed out.  Wondering if my connection was just to weak or something, I tried another Google search, and it worked just fine.  So for some reason, I can access Google.com, and that's it.  I found different solutions on the internet, some in the forums here, but they require the Ubuntu box to be hooked up to a different internet connection to download fixes and what-not.  Since my wireless connection is my only means of internet of here in the sticks, I'm stuck between a rock and a hard place with no obvious solutions.

Can anybody give me some advice here, or perhaps direct me to an idiots guide for getting my PPC internet to work with Ubuntu over USB?  Just seems strange, as it loads Google, but nothing else.  Like I said, I'm a complete NOOB with Ubuntu.

Thanks for any help!

Qkzoo

**Edit:**

I found the solution to this in another thread here in the forum after some good digging.  The thread is here: [http://ubuntuforums.org/showthread.php?p=2545109#post2545109](http://ubuntuforums.org/showthread.php?p=2545109#post2545109)

---

### Post by qkzoo on 2009-12-19
> 
 				 				**Re: Can only access google on Internet** 			
 			 			 		   		 		 		Ok, now for the tough part. You see, the next time you boot that machine, you're probably going to have the same problem. So unless you want to manually type that command in every time you boot, we need to sort out how to set that value automatically.

Here's the problem: I don't see any option in the DHCP configuration to manually force a given MTU value. I know how to set it for static IP's, but not DHCP.

What I can suggest (in a terminal window)
 	Code:
 	sudo nano /etc/init.d/rc.local 
And add, as the 2nd line in the script, the command:
 	Code:
 	ifconfig eth0 mtu 1400 
This probably isn't the "proper" way to handle this situation, but it's the only one I can think of off the top of my head.

Hopefully this will either provide you a permanent fix, or somebody with a better knowledge of DHCP will wander by with info on how to set the MTU via the DHCP configuration...

Lloyd B.


I can't respond to the original thread as it's locked.  The instructions here say "And add, as the 2nd line in the script, the command:".  Here's what my file looks like:

# ! /bin/sh
### BEGIN INIT INFO
# blah blah
# blah
# blah
# blah


PATH=BLAH

Do I enter this line after PATH= or after the #?

Thanks

---

### Post by qkzoo on 2009-12-28
Okay, I finally have my tethered connection working, but I could still use a few answers if somebody could give me a hand.  Here is the solution

1. I connect my phone via USB cable to the PC.
2. I load Terminal and type the following: "sudo ifconfig eth2 mtu 1000"
3. Internet now works.  If I disconnect the phone for any reason, I have to follow steps 1 and 2 all over again.

Although it's a bit annoying to have to type the command every time I hook my phone up, this is a working solution.  Here's my follow up questions to this situation:

1. Why do I have to type this command at all, shouldn't this stuff be built in?
2. Is there a way to automate this, so that when I plug my phone in, the system will execute the "sudo" command above automatically?

Thanks in advance,

Q

---

### Post by qkzoo on 2009-12-31
Bump.

Anybody?

---

### Post by Iowan on 2009-12-31
Do you happen to have a connection for eth2 set up in Network Manager? On rare occasions my Jaunty will connect to wired and wireless, but always connects to wired as soon as it is plugged in.

---

### Post by qkzoo on 2009-12-31
It connects automatically, I don't have to do anything other than plug it in; that was the easy part.  The part I don't understand, is why I always have to type "sudo ifconfig eth2 mtu 1000" into Terminal after it connects each time.  If I don't do this, the only site I can connect to is Google.

Hold on: I just checked the network settings and found that I can edit the MTU setting manually in the connection, which apparently it automatically added the connection.  Sweet, now I don't have to manually set it each time.  You rock!

---

### Post by Iowan on 2010-01-01
> **qkzoo said:**
>  You rock! It appears that you did all the work yourself... but glad you found a solution!

---

