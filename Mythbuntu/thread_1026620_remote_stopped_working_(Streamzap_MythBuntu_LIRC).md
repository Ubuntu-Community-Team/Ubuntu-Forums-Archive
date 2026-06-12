---
title: "remote stopped working (Streamzap MythBuntu LIRC)"
date: 2008-12-31
forum: Mythbuntu
---

### Post by davidstoll on 2008-12-31
I have a streamzap remote control that was mostly working (not all the buttons) and all of a sudden it just doesn't work any more.  The only thing I can think of is there were some updates that installed through the update manager (which I allowed).  But I can't be sure that is the exact moment it stopped working.

I also have an MCE USB remote that I would prefer to use if possible (it has more buttons).

The little IR receiver box blinks when I hit buttons, so it is alive.  I also read that I should replace the batteries even if the IR receiver blinks.  That didn't help.

I also did an update (to the same version) of lirc.  That didn't help either.

What are the steps I need to go through to see what is wrong and to get it back up and running?

---

### Post by laceration on 2008-12-31
The thing that will often mess up lirc is the drivers. It is better to reinstall the drivers.  If you did not install the drivers with dkms, a kernel update could have caused the problem  But first to make sure it is a lirc issue and not mythbuntu, open a terminal and type in
```
irw
```
and press some keys on your remote.  If it is working it will look something like this
```
000000037ff07bf2 00 Home mceusb
```

---

### Post by davidstoll on 2009-01-01
> **laceration said:**
> The thing that will often mess up lirc is the drivers. It is better to reinstall the drivers.  If you did not install the drivers with dkms, a kernel update could have caused the problem  But first to make sure it is a lirc issue and not mythbuntu, open a terminal and type in
```
irw
```
and press some keys on your remote.  If it is working it will look something like this
```
000000037ff07bf2 00 Home mceusb
```

Cool, I didn't know about that command.

Both my Streamzap and MCEUSB show button presses...separately of course and when each is appropriately configured in the Mythbuntu control centre.

It still doesn't work in myth.
Even when it was working, not all the buttons worked.  If I can get this to work in myth again, I'd like to know how to configure the remote so that more of the buttons work and how to customize them.

What's my next step?

---

### Post by davidstoll on 2009-01-01
> **davidstoll said:**
> Cool, I didn't know about that command.

Both my Streamzap and MCEUSB show button presses...separately of course and when each is appropriately configured in the Mythbuntu control centre.

It still doesn't work in myth.
Even when it was working, not all the buttons worked.  If I can get this to work in myth again, I'd like to know how to configure the remote so that more of the buttons work and how to customize them.

What's my next step?

What a minute, I just rebooted and irw didn't work.
Then I changed the remote driver in the Control Centre...and then back...and it worked again.  Maybe something isn't starting up correctly.

---

### Post by laceration on 2009-01-01
The configuration file that tells what lirc to do with your remote key presses is **.lircc** this is usually in your home directory.  I suppose it could be somewhere in your root too.  If it is not in your home do a 
```
locate .lircc
```
Your .lircc may or may not have include statements like
```
include ~/.lirc/mplayer
```
That means it looks at those files for directives too.  Within those files and .lircc are a bunch of blocks like this:
```

begin
    remote = mceusb
    prog = mplayer
    button = VolUp
    config = volume +1
    repeat = 0
    delay = 0
end

```
The remote and button fields are the same that come up when you press them within irw. prog, for you would be mythbuntu or myth.  The config is the command specific to the program.  Consult the mythbuntu documentation for those.

Sorry I can't help you with anything mythbuntu specific because I have never used it.

---

### Post by davidstoll on 2009-01-02
> **laceration said:**
> The configuration file that tells what lirc to do with your remote key presses is **.lircc** this is usually in your home directory.  I suppose it could be somewhere in your root too.  If it is not in your home do a 
```
locate .lircc
```
Your .lircc may or may not have include statements like
```
include ~/.lirc/mplayer
```
That means it looks at those files for directives too.  Within those files and .lircc are a bunch of blocks like this:
```

begin
    remote = mceusb
    prog = mplayer
    button = VolUp
    config = volume +1
    repeat = 0
    delay = 0
end

```
The remote and button fields are the same that come up when you press them within irw. prog, for you would be mythbuntu or myth.  The config is the command specific to the program.  Consult the mythbuntu documentation for those.

Sorry I can't help you with anything mythbuntu specific because I have never used it.

Thanks laceration, that is actually a big help, I believe you have pointed me to the file I had been looking for.

Ok, I "sort of" understand the file structure.  I fiddled around with it but was not able to get something to work correctly.

I would like to associate the "<" and ">" keyboard commands with...
000000037ff07be4 00 Replay mceusb
000000037ff07be5 00 Skip mceusb

One thing that confused be was that there were several entries in the .lirc/mplayer file for Replay, but only one for Skip.

There are many unused keys on the remote that I would like to customize.  There are actually several keyboard "mappings" (if that is what it is called) that I would like to make, but if I can get < and > to work, I'm hoping I can figure out the rest.

Any suggestions on this?

---

### Post by laceration on 2009-01-02
I take it that mythbuntu uses mplayer so you are setting up mplayer?  If so there is a file named input.conf in you /home/your-user/.mplayer/.  It is possible this file is somewhere else, do a locate if you have to.  This file has a key followed by a command.  You can find the command you want and put it in the config area of your .lirc/mplayer.  There are plenty of commands to find there if you still have the default file.  If you need to find more try
```
man mplayer
```

---

### Post by davidstoll on 2009-01-02
> **laceration said:**
> I take it that mythbuntu uses mplayer so you are setting up mplayer?  If so there is a file named input.conf in you /home/your-user/.mplayer/.  It is possible this file is somewhere else, do a locate if you have to.  This file has a key followed by a command.  You can find the command you want and put it in the config area of your .lirc/mplayer.  There are plenty of commands to find there if you still have the default file.  If you need to find more try
```
man mplayer
```

Based on your suggestion to take a look at input.conf, it makes sense that it would be in the users directory.  That way each user can have a custom configuration.  I did not have one in my home path.  Mine was in /etc/mplayer/, so it struck me as odd, but oh well.  I'll try to configure it tonight.

If I understand correctly, I use the input.conf file to find the command that needs to be executed and use irw to find the button I want to associate with that.  Take those two pieces of information and put it in the ~/.lirc/mplayer file...?


Also,

In my ~/.lirc/mplayer file, there are entries that say...
    remote = dish1

There are entries for dish1 to dish16...sometimes multiples of each and I don't see a pattern for their usage.  What does "dishXX" mean?

Thanks again!

---

### Post by laceration on 2009-01-02
Configuration files in a linux system can be set at system level, like in /etc, or at the user level.  The user level gets checked first and if not there it goes to system.  Think about it, this makes a lot of sense.

> If I understand correctly, I use the input.conf file to find the command that needs to be executed and use irw to find the button I want to associate with that. Take those two pieces of information and put it in the ~/.lirc/mplayer file...?

I think you got the idea.

is it
```
remote = dish1
```
or
```
#remote = dish1
```
the "#" means it is a comment.  If it is not commented out it is something I do not know about--and I thought I knew everything;)--and I would comment it out because it might break the file.

---

### Post by davidstoll on 2009-01-02
> **laceration said:**
> Configuration files in a linux system can be set at system level, like in /etc, or at the user level.  The user level gets checked first and if not there it goes to system.  Think about it, this makes a lot of sense.


I think you got the idea.

is it
```
remote = dish1
```
or
```
#remote = dish1
```
the "#" means it is a comment.  If it is not commented out it is something I do not know about--and I thought I knew everything;)--and I would comment it out because it might break the file.

No, nothing is commented out except the header info.

Basically, notice that there will be a "remote = dish16" command entry for a particular button/action.  There will be a duplicate entry for the same button/action, except it will be "remote = dish14" or dish15, etc.

Seems strange to me.
I have attached the file.

---

### Post by laceration on 2009-01-02
Sorry I misunderstood, I thought it was at the top the file or something.  It does say > Auto Generated by Mythbuntu Lirc Generator 
It could just be a sample file that needs to be fleshed out with the proper values or one that was generated improperly--like for the dish network??  I don't know how Mythbuntu works so maybe there is a reason for it, but that seems unlikely. The remote names that came up in irw are what you use.  You might check out the mythbuntu documentation.

---

### Post by davidstoll on 2009-01-07
> **laceration said:**
> Sorry I misunderstood, I thought it was at the top the file or something.  It does say  
It could just be a sample file that needs to be fleshed out with the proper values or one that was generated improperly--like for the dish network??  I don't know how Mythbuntu works so maybe there is a reason for it, but that seems unlikely. The remote names that came up in irw are what you use.  You might check out the mythbuntu documentation.

Now all of a sudden the irw command isn't showing any button presses.

What do I do now?

---

