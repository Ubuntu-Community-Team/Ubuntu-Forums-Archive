---
title: "No hostname in Ubuntu / sudo: unable to lookup via gethostbyname()"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by aleoje on 2006-06-03
Guys,

I am a complete linux newbie, but I am a fearless one, and of course problems happen when you have such combination. I want to summarize what happen to me in the hope that it would assist someone else.

This is what I did, stupid, yes. Objetive, none whatsoever:

System > Administration > Networking > (enter password) > General > delete hostname > OK

I figured my own name as my hostname was insecure and in my feverish windows mind I though no hostname was a great idea. Well, what happens next you probably all guessed. I rebooted and no network, no internet, no nothing. I couldn't even open the network screen again, not even Synaptic Package Manager worked anymore. It was like I obliterated my wonderful Ubuntu installation I had mananaged to install being a Windows user, and of which I was so proud, in one "Shock and Awe" blow. I didn't think I could, but I managed to!

Well, 7 days later I still had not fixed the problem. The reason is that it is not as simple as going back to the network screen mentioned above, it would simply not open, it waits forever. So you cannot undo by typing another new hostname again.

The message that I got while booting was:

"impossible de rechercher l'adresse pour.
cela empêchera Gnome de fonctionner correctement. il est possible de corriger le problème en ajoutant au fichier /etc/hots.
se connecter quand même réessayer "

only that in English (more about the French later). It kind of translates to "Impossible to obtain the ip address for .
This will not allow Gnome to function correctly. It is possible to correct this problem by adding to the file /etc/hosts.
Would you like to connect anyways?" 

Well, let me think. What are my options... hmmm... ok, let's try anyways.

I had already learned in my two weeks of Linux experience that you need to use sudo and gedit to access important protected files. Or files that need root access as I learned later.

However, 

sudo gedit /etc/hosts

does not work. Why what I found to be my salvation for every other file did not work?

Because:

sudo: unable to lookup via gethostbyname()

So, this newbie is going in circles. I need to restore the hostname, but I can't, because the tool to fix it needs a hostname! (?)

Also, please note that at this point I am only concentrating on /etc/hosts, didn't even consider to touch /etc/hostname because the message indicated the problem may be fixed by adding to HOSTS.

In my desperation, having read every post in English I tried to Google in different languages, that's when I found:

[http://forum.ubuntu-fr.org/viewtopic.php?pid=318837](http://forum.ubuntu-fr.org/viewtopic.php?pid=318837)

In it, our French friends discover that it is not really only adding to hosts that you fix the problem but by ALSO adding the hostname again to the file, you guessed it, /etc/HOSTNAME (capitals added for emphasis).

But even when I had a theoretical solution, the problem still remained on how to fix it. 

I prayed. Yes, I am a practicing Catholic and I found out through the years that prayers and supplication to God help me greatly with my computer, and any other problem for that matter. The Rosary, by the way, is a great tool to calm you down while dealing with widows problems like blue screens or general slowness, security updates and spyware.

God made me stumble with this: (Thank you, Jesus, I love you!) :)

[http://www.ubuntuforums.org/showthread.php?t=91455&page=2](http://www.ubuntuforums.org/showthread.php?t=91455&page=2)

In it Mustard describes how to enter into recovery mode and edit the files that need root access.

So, I added my new hostname (which is not my name anymore) to the end of the first line of my /etc/hosts file as Mustard describes AND using the same procedure added the same single word to the first line of /etc/hostname which was completely blank.

When rebooted I had my installation back, with no annoying message. If I may humbly transmit my opinion to the Ubuntu developers, I would derive the following commandment:

"Thou shall not let the newbies obliterate your OS in one blow"

You may say, I had to access the network screen by typing my password, and this is true, but the consequences are too far reaching for such a simple error that any true fearless newbie like me can make.

These are my 2 cents to make this a better world. If this helps you I would love to hear from you to know how many like me are out there. Or am I the only one to do such brilliant things??

Remember to pray often! :)
May God bless you all.

Alejandro

---

### Post by croak77 on 2006-06-04
Instead of gedit try anf see if 'sudo nano -w /etc/hosts' works.

---

### Post by GMNesje on 2006-06-17
thank you !!!!!!
I managed to do the same thing as you did, thought i had to reinstall but thanks tou you i got it fixed!!

i restarted in recovery mode, and edited /etc/hosts and /etc/hostname, using nano.

---

### Post by waggotamp on 2006-07-13
I'm not sure if I have the same problem , but my host name is there in nano - but I'm unable to start any down loads - it does not ask for the password anymore and I cannot upgrade. I get this message when using nano. 

  GNU nano 1.3.10             File: /etc/hosts                        Modified

127.0.0.1 localhost.localdomain localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts










                [ Error writing /etc/hosts: Permission denied ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

---

### Post by foots2015 on 2006-07-13
Heh had the same problem. Solved by reinstalling dapper :)

---

### Post by AZzKikR on 2006-07-14
I once had about the very same problem occuring on my server rig. It was put away deeply somewhere, with no monitor, keyboard or mouse attached so it was a pain in the a$$ to get it out, attach a monitor to it and find out what the hell happened!

What happened was, I changed my hostname to something else (by editing the /etc/hostname file or whatever it's called), and thinking that was sufficient, I rebooted. 

Suddenly, SSH didn't function, my website was offline, FTP did not work etc. I connected a monitor and keyboard and decided to investigate. I wanted to edit something using sudo, and I got the message you said. Totally freaked out, because I couldn't edit anything anymore which belonged to user and group 'root'! I thought I fixed it by putting in an Ubuntu Live DVD and editing the file straightly on the file system, but I can't recall that anymore... 

Nowadays, when I install an Ubuntu server system I delibarately activate the 'root' user, to (I think) avoids this sudo problem.

---

### Post by amontford on 2006-09-22
I had the same problem and wanted to add a small thing.  Typing `hostname -f` returned localhost.blah.blah instead of Marlin.blah.blah which it should have.  So I added Marlin.blah.blah to be before localhost.blah.blah in the /etc/hosts file and fixed it for me.  I couldn't ssh to my server without this either.  Very strange....

now it says: 
127.0.0.1    Marlin.blah.blah localhost.blah.blah localhost Marlin

---

### Post by qwerty987 on 2008-02-19
> **AZzKikR said:**
> I once had about the very same problem occuring on my server rig. It was put away deeply somewhere, with no monitor, keyboard or mouse attached so it was a pain in the a$$ to get it out, attach a monitor to it and find out what the hell happened!



try 
sudo -s
to get root. I get the "unable to lookup ... via gethostbyname()", but still logged in as root to fix the hostname issues. Saved me from find the keys to the server room...

---

### Post by Iowan on 2008-02-19
[Change hostname]("http://ubuntuforums.org/showthread.php?t=232839&highlight=gethostbyname%28%29").  My **/etc/hosts** file:```
127.0.0.1 localhost
127.0.1.1 machine1.mynet

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by tom93 on 2008-03-23
> **aleoje said:**
> ... I found out through the years that prayers and supplication to God help me greatly with my computer, and any other problem for that matter. The Rosary, by the way, is a great tool to calm you down while dealing with widows problems like blue screens or general slowness, security updates and spyware...
Thank you for this post ! Not only did it help me with my hostname issue, but it had me rolling on the floor laughing !:lolflag:

---

