---
title: "Problem in prepping MediaMVP for Mythbuntu install. Please help"
date: 2008-12-30
forum: Mythbuntu
---

### Post by gayedonn on 2008-12-30
I have been systematically been following  the instructions for Hauppauge MediaMVP as a Mythbuntu Frontend but have struck an error, something is missing and I can't find what it is.

This is where I got stuck:

[https://help.ubuntu.com/community/MythTV/MediaMVP_Frontend#Customize%20dongle.bin.config]("https://help.ubuntu.com/community/MythTV/MediaMVP_Frontend#Customize%20dongle.bin.config")
[COLOR=Blue]Now we can set up atftpd to run as our mvpmc daemons. For simplicity, we'll put them in /etc/rc.local, so they run at boot. While we are editing /etc/rc.local, we will also add a command to launch another program we will add later.

$ sudo nano /etc/rc.local

Before the exit 0, add:

/usr/sbin/atftpd --daemon --port 16869 --retry-timeout 120 \
--mcast-addr 192.168.1.0-255 --mcast-ttl 2 --verbose=7 /tftpboot

/usr/sbin/atftpd --daemon --port 69

/usr/bin/mvprelay 16881 5906 6337 192.168.1.100 &

You may need to change --mcast-addr 192.168.1.0-255, depending on your network configuration. The example is valid for backends ips anywhere in the 192.168.1.xxx range. If your backend ip is 192.168.2.xxx or 192.168.0.xxx, etc. then you need to change it to --mcast-addr 192.168.2.0-255 or --mcast-addr 192.168.0.0-255 -- also remember to replace 192.168.1.100 with the address of your backend server.

It should look similar to this when you are finished:

#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/sbin/atftpd --daemon --port 16869 --retry-timeout 120 \
--mcast-addr 192.168.1.0-255 --mcast-ttl 2 --verbose=7 /tftpboot

/usr/sbin/atftpd --daemon --port 69

/usr/bin/mvprelay 16881 5906 6337 192.168.1.100 &

exit 0[/COLOR]

The following line [COLOR=Blue]'/usr/bin/mvprelay 16881 5906 6337 192.168.1.100 &'[/COLOR] causes a file not found!  I tried to move the mvprelay the directory but because it is owned by the root it is giving me much grief :confused:
Also while I'm here can I install Mythbuntu (the latest Alpha 2 version) onto my second hard drive and use it there? If so how should I do this, I mean do I make it a primary drive or an extended drive?

Oh ... and I am using Ubuntu 8.10 Gnome AMD 64-bit and loving it totally ditched Microsoft! :cool:

cheers guys

---

### Post by tgm4883 on 2008-12-30
I fixed your title in hoping more people with MediaMVP's would see it now.

---

### Post by gayedonn on 2008-12-30
> **tgm4883 said:**
> I fixed your title in hoping more people with MediaMVP's would see it now.

Thanks heaps for that.
Hopefully the guy who wrote the documentation might see it and be able to help!
cheers

---

### Post by gayedonn on 2008-12-30
[FONT=Comic Sans MS][COLOR=Blue][SIZE=3]Where are all the gurus????
[/SIZE](edited as not too offend)
[/COLOR][/FONT]

---

### Post by tgm4883 on 2008-12-30
> **gayedonn said:**
> [-X[FONT="Comic Sans MS"][COLOR="Blue"][SIZE="3"]Seems pretty shameful that one would have to offer money to generate any assistance!
Where are all the gurus????
I don't wish to offend anyone it is just an observation. I can't finish what I have started and it's frustrating not getting anywhere.[/SIZE]:-\"](*,)[/COLOR][/FONT][SIZE="3"][/SIZE]

I'd like to point out that your original post is less than 6 hours old.  Not everyone checks this forum everyday, and many people live on the other side of the planet.  You are also having a problem with a device that I would venture not that many people have.  On top of that, this is a forum, where instant answers rarely happen, and everyone on this forum is a volunteer and not paid for the support they give.

You should bump your post no more than 1 time per 24 hours.  By bumping, I mean posting again to get this post to the front page again.  You can reply to people, but don't keep posting just to draw attention to yourself.

---

### Post by gayedonn on 2009-01-02
[COLOR=Blue]:frown:[/COLOR]
[FONT=Comic Sans MS][SIZE=2][COLOR=Blue]There must be some one else out there using a Hauppauge MediaMVP for Mythbuntu.[/COLOR][/SIZE][/FONT]

---

### Post by gayedonn on 2009-01-06
:x
 [FONT=Comic Sans MS][COLOR=Blue]I am so glad I have persisted myself and I think I may have solved the problem I had with the MediaMVP issue.
This does not change the fact that my questions regarding the 2nd hard drive have been left unresolved. It leaves a bitter taste in my mouth that nobody that viewed my thread either had not read it properly or just could not be bothered to help.
Thanks for nothing guys!!!  [/COLOR][/FONT]=D>

---

