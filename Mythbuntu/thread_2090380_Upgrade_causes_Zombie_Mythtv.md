---
title: "Upgrade causes Zombie Mythtv"
date: 2012-12-02
forum: Mythbuntu
---

### Post by atcrank on 2012-12-02
Hi all,

[I am about to boot over to Windows for my wife to watch TV as I've broken mythtv at a critical time).

I was getting on alright in 11.04, but wanted to update, so used the update manager to go to 11.10 and then 12.04.  During the updates everything went well, the only notable feature being that I gave a new password for Mysql's mythtv user.

While going through some changes to do with the reasons for updating, my system clock got out of sync with the world. Mythtv recorded a couple of hours in the middle of the day as if it was tonights shows.  I was not able to forget these recordings or override so as to force new ones.

I started Mythbuntu control centre hoping to use it a bit like dpkg - just to straighten things out.  

After running it a couple of times I now have three unkillable Mythbackend processes.  When I open Mythtv-setup, I get both "Mythbackend is still running" AND "Can't connect to Mythbackend, is it running?" messages, comically overlaid.  The timestamps on the ps -e reports are usually very low e.g. 00:00:02, but I'm not sure if that just means that they started at startup or what?

Any help?  I probably won't get back on for 24hrs (Windows, as I said).  I assume this is just a noob mess for which I should raze everything to the foundations and start over, but if there's something smart to get me out of a jam I'd appreciate the help.

---

### Post by tgm4883 on 2012-12-02
> **atcrank said:**
> Hi all,

[I am about to boot over to Windows for my wife to watch TV as I've broken mythtv at a critical time).

I was getting on alright in 11.04, but wanted to update, so used the update manager to go to 11.10 and then 12.04.  During the updates everything went well, the only notable feature being that I gave a new password for Mysql's mythtv user.

While going through some changes to do with the reasons for updating, my system clock got out of sync with the world. Mythtv recorded a couple of hours in the middle of the day as if it was tonights shows.  I was not able to forget these recordings or override so as to force new ones.

I started Mythbuntu control centre hoping to use it a bit like dpkg - just to straighten things out.  

After running it a couple of times I now have three unkillable Mythbackend processes.  When I open Mythtv-setup, I get both "Mythbackend is still running" AND "Can't connect to Mythbackend, is it running?" messages, comically overlaid.  The timestamps on the ps -e reports are usually very low e.g. 00:00:02, but I'm not sure if that just means that they started at startup or what?

Any help?  I probably won't get back on for 24hrs (Windows, as I said).  I assume this is just a noob mess for which I should raze everything to the foundations and start over, but if there's something smart to get me out of a jam I'd appreciate the help.

Not sure what you did in Mythbuntu Control Centre.

The processes are not unkillable. They would die with a kill -9, and a reboot would also kill them (and just start it once when starting).

Once you have it starting once, then lets see what issues you have.

---

### Post by atcrank on 2012-12-02
Thanks - you are right - after rebooting there is just one Mythbackend, and the frontend can see it and the database.  At first this morning I still couldn't set new recordings. It was as if I had read-only access.  I experimented with dpkg --configure mythtv, but got a 'this is already configured' and 'there was an error (running dpkg).'

I looked through various settings, but only changed 'localhost' to '127.0.0.1' in the frontend settings.
Now it all seems to be working and I've really no idea what the problem was or how it has been fixed.  Dagnammit.  Thanks for responding; really appreciate the voice of reason in these situations.

---

### Post by atcrank on 2012-12-03
I think the problem might be which user is running mythbackend and mythfrontend - starting up this afternoon it was back to a weird, read only access to mythconverg and thought the master backend must be hung or not present.  I sudo ran mythtv-setup which stopped that version and launched a new one on completion, and after that, all is well. I guess I need to look at startup stuff.

---

### Post by tgm4883 on 2012-12-03
During install, what did you name your user?

---

