---
title: "Front end not starting"
date: 2009-04-25
forum: Mythbuntu
---

### Post by kc2dqp on 2009-04-25
Ok, I'm a total noob here, but I've scanned the forums here, and can't seem to find an answer to whats happening here or why. First off, trying to find documention on setting up a front end, no bells and whistles, just a front end is HARD. It's like VERY little documention is out there on this. Second, I have set it up, with the best docx. I can find, but when it boots, it goes to the mythbuntu desktop and wont boot the front end for nothing. I check the logs, but it seems as though I am not looking at the correct log. Additionally, when I use the manual start of up 'mythtv', it gets maybe 7 lines into what looks like the startup and then freezes. I am using Version 8.10, on a 1.2 cel. 512 ram, 40gig hd. I know the min. requirements are short, but this is just a no frills FE and I can't seem to get it to play anything. Can anyone shed some Ideas to this goal of mine? I LOVE my working FE/BE, just need to get other FEs working..

Thanks in advance-

---

### Post by klc5555 on 2009-04-25
> **kc2dqp said:**
> Ok, I'm a total noob here, but I've scanned the forums here, and can't seem to find an answer to whats happening here or why. First off, trying to find documention on setting up a front end, no bells and whistles, just a front end is HARD. It's like VERY little documention is out there on this. Second, I have set it up, with the best docx. I can find, but when it boots, it goes to the mythbuntu desktop and wont boot the front end for nothing. I check the logs, but it seems as though I am not looking at the correct log. Additionally, when I use the manual start of up 'mythtv', it gets maybe 7 lines into what looks like the startup and then freezes. I am using Version 8.10, on a 1.2 cel. 512 ram, 40gig hd. I know the min. requirements are short, but this is just a no frills FE and I can't seem to get it to play anything. Can anyone shed some Ideas to this goal of mine? I LOVE my working FE/BE, just need to get other FEs working..

Thanks in advance-

If you're manually starting it up, then the command from the terminal will be 'mythfrontend', not 'mythtv'. You should not have mythbackend nor mysqld running on this frontend-only machine, since it has no tuners in it. At best, running these programs on the frontend-only machine will uselessly consume resources, at worst it can cause some corruption to your mysql data if you connect successfully to your master backend with these programs running.

When you run mythfrontend from a terminal, the terminal should initially complain about no backend and no mysql errors, and then throw up the mythfrontend configuration screens. Here you'll choose the language, then give it the ip address (not 127.0.0.1) of the master backend machine, and the mysql password of the mythtv user on that machine. When this is done, mythfrontend will go out and try to connect with the master backend using the address and the password you gave it. If it succeeds, you're done --if it fails, it dumps you back to the configuration screens.

This means that you will have had to properly configure the backend on your master backend machine before you set up your frontend. In the myth control center on that backend machine, you'll need to indicate that the mysql installation should be set to allow remote connections (as a "master backend"). In addition, in the backend setup, in the "General" section, all occurrences of localhost (127.0.0.1) need to be replaced with the actual address of this backend machine on your network (usually 192.168.1.something or 10.0.2.something). 

When these steps have been taken and your backend restarted, then mythfrontend can be run and configured on the remote frontend machine, and it ought to have no difficulty connecting.

Once you get the hang of setting up a frontend, it goes quickly. I set one up yesterday with 9.04 on an old T23 Thinkpad with a wireless "g" card, connecting to my master backend running 7.10. The longest part of the process was downloading the mythtv packages (and disabling mythbackend and mysqld) on the laptop. Works beautifully for analog and SD.  

Good luck! :)

---

### Post by utar on 2009-04-25
You don't say if you are using mythbuntu or installing myth on regular ubuntu?

---

### Post by kc2dqp on 2009-04-27
Sorry, I wasn't clear on that- 

I am using the off the shelf Mythbuntu 8.10

I am I think just having a hard time trying to connect to the B/E from any F/E other than the F/E B/E box.:confused:

Thanks for the help.

---

