---
title: "Problem running mythbackend"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by hansoffate on 2007-04-01
I had my whole system working.  Then I had a power outage.  Since I brought it up, my tv tunner card wasn't working.  I was messing around and I took out the external channel changer script that used to work, and now at least 1 channel works (no channel changging)

When I put it in the channel changer script, it doesn't work again.  

Here is my log file that i put on pastebin.

[http://pastebin.ca/419897](http://pastebin.ca/419897)


Thanks for the help
-Hans

---

### Post by superm1 on 2007-04-01
Hans,

You need to mark the script as executable.

sudo chmod +x SCRIPT_NAME

Also, your database is a mess there.  It sound like when the power went out - it was in the process of writing some stuff to disk and corrupted the database.  Easiest way to fix it is installing phpmyadmin and then repairing the table from there.

---

### Post by hansoffate on 2007-04-01
superm1- I ran that command with ssh.  When my girlfriend is done with her show/shows I'll test out tv again.

Also, I installed phpmyadmin, but what credentials should i login with?  Also, is there a way to lookup what passwords there are?  Because I tried logging in with "root" and i tried some passwords but they didn't work. 

And when you say "repair"  what do you mean by repair?

Thank you for your help
-Hans

:Edit: i logged in as mythtv, and did "Repair Table" to everythign for mythconverg.  I hope that is what i was supposed to do.  I got alot of warnings and skipped.  Is that ok?

---

### Post by superm1 on 2007-04-01
> **hansoffate said:**
> superm1- I ran that command with ssh.  When my girlfriend is done with her show/shows I'll test out tv again.

Also, I installed phpmyadmin, but what credentials should i login with?  Also, is there a way to lookup what passwords there are?  Because I tried logging in with "root" and i tried some passwords but they didn't work. 

And when you say "repair"  what do you mean by repair?

Thank you for your help
-Hans

:Edit: i logged in as mythtv, and did "Repair Table" to everythign for mythconverg.  I hope that is what i was supposed to do.  I got alot of warnings and skipped.  Is that ok?
Hans,

You'll have to see how the database fairs after the repair.  You did do it right.  If it is still giving errors, your only option will be to restore a backup of it (if you have one), or to drop the database and reinstall it.

---

### Post by hansoffate on 2007-04-01
The table seems to be repaired.  Everything in my EPG seems to be correct.  TV is working but channel changing doesn't work.  Here is an excerpt from the log.
```

sh: /usr/local/bin/change-channel-lirc.pl: Permission denied
2007-04-01 12:56:43.448 ret_pid(10580) child(10580) status(0x7e00)
2007-04-01 12:56:43.452 ChannelBase: external tuning program exited with error 126
sh: /usr/local/bin/change-channel-lirc.pl: Permission denied
2007-04-01 12:56:44.472 ret_pid(10582) child(10582) status(0x7e00)
2007-04-01 12:56:44.476 ChannelBase: external tuning program exited with error 126
2007-04-01 12:56:44.483 TVRec(1) Error: Setting start channel '3' failed, 
                        and backup '3' failed as well.
```

Any ideas?  I did that command to the channel changer.

Here is my ls -l
-rw-r--r-- 1 root root    689 2007-03-22 15:40 change-channel-lirc.pl
-rw-r--r-- 1 root root    699 2007-03-22 02:06 change-channel-lirc.pl~

Thanks for the help
-Hans

---

### Post by superm1 on 2007-04-01
For some reason, that command isn't setting the file to be executable.

The results should look like this:

```
cd /usr/local/bin/
ls -l change*
-rw-r--r-- 1 root root    689 2007-03-22 15:40 change-channel-lirc.pl
-rw-r--r-- 1 root root    699 2007-03-22 02:06 change-channel-lirc.pl~
sudo chmod a+x change*
ls -l change*
 -rwxr-xr-x 1 root root    689 2007-03-22 15:40 change-channel-lirc.pl
 -rwxr-xr-x 1 root root    699 2007-03-22 02:06 change-channel-lirc.pl~

```
The a+x means all users, set executable.

---

### Post by hansoffate on 2007-04-01
```
2007-04-01 13:43:26.730 ret_pid(0) child(12770) status(0x0)
irsend: command failed: SEND_ONCE Hauppauge 6
irsend: unknown remote: "Hauppauge"
2007-04-01 13:43:27.733 ret_pid(0) child(12770) status(0x0)
irsend: command failed: SEND_ONCE Hauppauge 1
irsend: unknown remote: "Hauppauge"
2007-04-01 13:43:28.741 ret_pid(0) child(12770) status(0x0)
irsend: command failed: SEND_ONCE Hauppauge 2
irsend: unknown remote: "Hauppauge"
2007-04-01 13:43:29.749 ret_pid(0) child(12770) status(0x0)
irsend: command failed: SEND_ONCE Hauppauge ENTER
irsend: unknown remote: "Hauppauge"
2007-04-01 13:43:30.757 ret_pid(12770) child(12770) status(0x0)
2007-04-01 13:43:30.763 External Tuning program exited with no error
```

Now I am getting this.  What should I do?  I don't get why this was working, and now isn't.

Thank you for the help
-Hans

---

### Post by superm1 on 2007-04-01
Check out your /etc/lirc/lircd.conf.

Perhaps it was corrupted in the process.

---

### Post by hansoffate on 2007-04-01
Everything looks fine.  Doesn't seem corrupted.  What should I do?

Thank you for the help,
-Hans

---

### Post by hansoffate on 2007-04-02
Bump?  Tv changing doesn't work still.

Thanks
-Hans

---

### Post by superm1 on 2007-04-02
Hans,
Did you attempt to reinstall lirc from source in the process here (or ever)?  If /etc/lirc/lircd.conf is correct, for some reason its not being parsed.  This is a common side effect of a source installation.

---

### Post by hansoffate on 2007-04-02
MajorIdiot helped me install this from a patched pvr150 package that was built for another distro.  Since then, he and I think you, helped release a new package for ubuntu.  Should I remove what we did and try to use the package?  Or, should I just wait for major idiot?

If you think I should remove lirc and try to reinstall with the new ubuntu package, how would i remove it?

Thank you for the help,
Hans

---

### Post by superm1 on 2007-04-02
> **hansoffate said:**
> MajorIdiot helped me install this from a patched pvr150 package that was built for another distro.  Since then, he and I think you, helped release a new package for ubuntu.  Should I remove what we did and try to use the package?  Or, should I just wait for major idiot?

If you think I should remove lirc and try to reinstall with the new ubuntu package, how would i remove it?

Thank you for the help,
Hans
Ah your the one he was working with.  I put the package together for Ubuntu and he put together all of the surrounding files and wrote the guide for it.
I'm not sure how he went about helping you get set up with things previously, but that does seem the ideal way to go.  If something is broken with regard to lirc, using the Ubuntu package for it is always the smarter way.

I'll have to get him to join in on this thread to help with regard to cleanup of the package he setup with you.  I'll ping him.

---

### Post by hansoffate on 2007-04-02
Yeah, I am the one he was working with.  Thanks for setting up the package.  I am sure I will use it when I build my next PVR system (probably in the summer).

I sent him a PM and gave him SSH information for him to take a look around while I am at school/work.  I am done with work in about 10 minutes and will be checking the forums again in about 3 hours from now (after class).  If you get in contact with him and you want to poke around and see whats going on, you can get the info from him.

Thanks for the help,
-Hans

---

### Post by hansoffate on 2007-04-03
I did what majoridiot told me to do and just reinstalled.
Here is my error that I get now when trying to run the frontend 
[http://pastebin.ca/422062](http://pastebin.ca/422062)
What should I do?


Thanks
-Hans

---

### Post by superm1 on 2007-04-03
> **hansoffate said:**
> I did what majoridiot told me to do and just reinstalled.
Here is my error that I get now when trying to run the frontend 
[http://pastebin.ca/422062](http://pastebin.ca/422062)
What should I do?


Thanks
-Hans
Sounds like the mysql server isn't running, or your IP address changed from that post.  Can you check both?

---

### Post by hansoffate on 2007-04-03
Yup.  I fixed the myql error.  I changed localhost to the ip when I should have left it to the localhost.  Now I don't get a DB connection error.  

At least the frontend starts now.  Now when I try to Watch TV, it says mythbackend isn't running.  

```
2007-04-03 00:17:20.959 Connected to database 'mythconverg' at host: localhost
2007-04-03 00:17:21.021 Connecting to backend server: 192.168.1.105:6543 (try 1 of 5)
2007-04-03 00:17:24.026 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.

```

I checked setup in both the frontend and the backend.  Any ideas?

Thanks 
-Hans

---

### Post by superm1 on 2007-04-03
First check and see if the backend is running.

Next check /var/log/mythtv/mythbackend.log.  Typically its very informative about why the backend would stop running.

---

### Post by superm1 on 2007-04-03
My best guess here-
Your on a home network that dynamically hands out addresses.  This computer happened to get a different address this time around and that threw a lot off.

---

### Post by hansoffate on 2007-04-03
I was stupid.   I set my static ip, i thought it changed.  It was still not that static ip that I set.  

I restarted and now it "works".

The tv card shows nothing but static even though its set to the correct channel.  Now, I am trying to get lirc configured for my PVR150 with IR Blaster and 

```
hansoffate@mythlinux:~$ wget http://people.atrpms.net/~mlimonciello/personal/80DF6D58.gpg -O- | sudo apt-key add -
--00:35:02--  http://people.atrpms.net/~mlimonciello/personal/80DF6D58.gpg
           => `-'
Resolving people.atrpms.net... 160.45.32.210
Connecting to people.atrpms.net|160.45.32.210|:80... failed: Connection timed out.
Retrying.

--00:38:17--  http://people.atrpms.net/~mlimonciello/personal/80DF6D58.gpg
  (try: 2) => `-'
Connecting to people.atrpms.net|160.45.32.210|:80... 
```

That's happening.
I wonder if it will be up tommorrow.  I just realized that is you.  Do you know if it is up?


Thank you
-Hans

---

### Post by superm1 on 2007-04-03
Looks like a lot of atrpms hosted sites are down (including my webspace and ivtvdriver.org).  I'll let Axel know.  Should hopefully be alive again tomorrow.

---

### Post by hansoffate on 2007-04-03
```
hansoffate@mythlinux:~$ wget http://people.atrpms.net/~mlimonciello/personal/80DF6D58.gpg -O- | sudo apt-key add -
--01:12:56--  http://people.atrpms.net/~mlimonciello/personal/80DF6D58.gpg
           => `-'
Resolving people.atrpms.net... 160.45.32.210
Connecting to people.atrpms.net|160.45.32.210|:80... failed: Connection refused.
gpg: no valid OpenPGP data found.

```

It should be working.  Why do I get an erorr?

Thank you for the help,
Hans

---

### Post by hansoffate on 2007-04-03
K.  Got it mostly fixed.  Channel 3 works but if i change channels, it goes to static. It seems as though my external channel changer script isn't working.

IRsend IS working and turning off the blaster.

i put in the channel change script under setup.  And i made it from the howto and changed the remote to "blaster".  I don't know what I am forgetting.  When checking the logs, when changing the channel, i don't see anything about it trying to blast my tv.

Any ideas on how to get this working?

Thanks
-Hans

---

### Post by superm1 on 2007-04-03
Ok, so you verified the script outside of myth then?  Is it actually "functioning" or just you see it flashing the IR diode?

---

### Post by hansoffate on 2007-04-03
I verified that my blaster code IS working.  I used ir send to poweroff my satbox, and it worked.  I just can't get my external channel changer working.

Thanks for the help
-Hans

---

### Post by superm1 on 2007-04-03
Have you marked your channel change script executable?  Are you sure it is being called (eg is in the right place of mythtv-setup)

---

### Post by hansoffate on 2007-04-03
It was pointing to the correct place, but at work I sshed in and found that it wasn't executable. I changed it to executable and I will test it when I get home tonight and see if its working.

Thank you for the help,
Hans

P.S.  I have looked for an ubuntu guide on how to make mythweb accessible out of your homenetwork.  I couldn't find one.  Is there one for this?  I think it may be just a matter of changing the domain it binds to from 127.0.0.1 to something else.  Any ideas?

---

### Post by hansoffate on 2007-04-03
I just got home and tried the frontend and still no channel changing.  It seems as though the script isn't being loaded.

I put /usr/local/bin/change-channel-lirc.pl as my external channel changer.  When checking my backend log, it doesn't seem to even be loaded.  When i try to chagne the channel, it doens't even try to use the script.  Maybe I am using the wrong script.  

Any ideas?
Thanks
-Hans

---

### Post by superm1 on 2007-04-04
Okay, well as long as the script is marked executable, does it work from command line as your regular user?  If so perhaps this problem is related to the permissions the mythtv account has to access devices that the script is calling upon.

I'm imagining that it will call upon /dev/lirc0 or something very similar.  Check and see the permissions for /dev/lirc0 (ls -l /dev/lirc0).  

As for it not being called by the backend at all, your sure that you have it entered in the correct input on mythtv-setup?

So under input-connections, you made sure that the input you were using is the only place you entered it.  
Also, do you need the tuner on this device preset to say channel 3?  If the external device you are changing channels on requires you to tune a tv to say channel 3, you need that box filled too.  If you are using a svideo or composite input however, this shouldn't be a concern.

Hopefully this all helps... Looking forward to getting this one nailed. ;)

---

### Post by hansoffate on 2007-04-05
Sorry for taking a while to post back.  I had school all day yesterday and had alot of other things to do. 

hansoffate@mythlinux:~$ ls -l /dev/lirc0 
crw-rw---- 1 root root 61, 0 2007-04-03 19:53 /dev/lirc0

I made sure i typed to the external channel changer script correctly.  /usr/local/bin/change-channel-lirc.pl 

I have both of the channel options to 3 (that is the one it needs to be on).  However, it works a bit differently then it should. Normally, when you have a preset channel to 3, the preset stays on that channel, and when you change a channel (let's say to channel 13) it would "change" to that channel, but the actual channel won't change.  However, you should still be able to see some sort of TV. 

My mythtv, however, when I change the channel to anything but 3, it goes to static, meaning that the preset channel isn't staying.  I think this is partially due to the script, however it is the one off the documentation, so it should work.  

I am sure that irsend/the ir blaster is working because i can manually IRSEND the power to the box and turn it on and off.  

Any ideas on what I should do?
Thanks,
Hans

---

### Post by hansoffate on 2007-04-05
superm1 took a look around.  It turns out changing "Use custom identifier for frontend preferences" under database configuration under frontend setup changed changes something in ~./mythtv/mysql.txt which made a conflict.

superm1 will post back what he did to fix it.

Thank you for the help,
Hans

---

### Post by hansoffate on 2007-04-05
Well, the channel changer works, however because I am using an svid connection I don't get any audio.  (is that true svid doesn't transfer audio?)  If so, how do I get audio  to the card?  If i try to switch it back to tuner 1, i get static.  Any ideas?

Thanks,
Hans

---

### Post by superm1 on 2007-04-05
> **hansoffate said:**
> superm1 took a look around.  It turns out changing "Use custom identifier for frontend preferences" under database configuration under frontend setup changed changes something in ~./mythtv/mysql.txt which made a conflict.

superm1 will post back what he did to fix it.

Thank you for the help,
Hans

From what it appears, this was a large mixup between which address tuners were actually assigned to.  It seemed that all changes were being applied to the backend as the hostname in ~/.mythtv/mysql.txt rather than the hostname the backend was initially setup as.  Moral of the story, don't use the unique identifier unless your hostname really does frequently change.  And then, only use them on frontends.

---

### Post by hansoffate on 2007-04-06
Audio works after I bought an RCA to 1/8th inc adapter and plugged it into line in.  AWESOME!

Thank you for the help,
Hans

P.S. Major idiot told me to change the screen size of mythtv recording so it records better.  Do you know what that is?  I remember making it bigger.

---

