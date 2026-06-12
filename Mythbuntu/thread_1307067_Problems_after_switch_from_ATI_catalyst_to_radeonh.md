---
title: "Problems after switch from ATI catalyst to radeonhd, upgrading kernel"
date: 2009-10-30
forum: Mythbuntu
---

### Post by inovermyhead on 2009-10-30
I'm not sure whether this is the right place to post this but here goes.  

I've been struggling to get satisfactory performance from my Mythbuntu 9,04 system for months now.  Among many challenges, I've never managed to get smooth playback on my 780G based board using the integrated ATI HD3200 GPU and an AMD 5050e CPU.  I tried a series of Catalyst driver versions all the way up to 9.9 but never quite got there.  I've wanted to try the open source drivers again and was waiting for the radeonhd driver to get to the point where it looked like it was worth giving it a go.  The radeon driver that I installed initially from the release 9.04 CD was a disaster performance wise which is why I had abandoned it in favor of the Catalyst driver.  That and the fact that I'm using HDMI digital audio output, and the radeonhd driver seemed to lag the radeon driver in terms of enhancements and fixes for quite some time.  

Last weekend I noticed the 1.3.0 version of radeonhd released in mid-September appeared to have everything I needed, potentially.  I installed it using the instructions I found here:[INDENT][http://www.x.org/wiki/radeonhd:INSTALL](http://www.x.org/wiki/radeonhd:INSTALL)[/INDENT]After reboot, things looked fairly promising to start with, much to my surprise.  HDMI digital audio continued to work with no issues just as it had with the Catalyst drivers.  ClearQAM SD channels played more smoothly than with the Catalyst drivers, although HD channels were much worse in that they basically played in slow motion and had my CPU maxed out, to the point where it barely responded to my remote.  All the same, it was progress of a sort and I resolved to verify that I had correct optimal settings and try some other tweaks.  First however, I decided to take a newly posted kernel update shown in update manager with security fixes.  This was the 2.6.28-16-generic, and it replaced my 2.6.28-15-generic.  

This is where things slowly began to get ugly.  When the box booted to the xfce4 desktop it took a lot longer than usual, and the desktop would flash several times before starting up mythfrontend automatically.  Mythtv continued to work normally, but on exiting mythfrontend my desktop had only icons on it, no menu bar across the top of my screen like usual.   I rebooted several times with the same result.  The only way to get to commands from my desktop was to right-click on the desktop and use the drop down menus from there.  I observed that initially while the desktop was starting up and apparently thrashing, flashing the screen, etc, the menu bar across the top would be there initially but after a few flashes would disappear leaving only the icons, then mythfrontend would eventually start automatically as usual.  After several hours of googling(on another machine) I finally found a solution to this problem when I found a post somewhere where someone seemed to be experiencing something very similar.  The recommendation was to delete the ~/.cache directory.  I tried this and rebooted and it did the trick.  My menu bar returned, and  my startup was now much faster than it had been in a long time.  I think this was because this process also cleared out some applications, like update manager and some Terminal windows which used to always start automatically on every boot even though I had tried everything I knew how to in "Session and Startup" to make them go away.  It had been stuck that way for a long time, long before I upgraded to radeonhd or the new kernel, and I had given up on it eventually.

Thinking I was now back in business, I went to pull up firefox and realized that my wireless was no longer working.  From the first day I installed 9.04 this is one thing that always just worked.  A reboot didn't cure it either.  No programs requiring network connection, like update manager, were working.  The wireless adapter was recognized, and the NetworkManager process was running, but still nothing.  So then I decided to start looking at logs.  I ran Mythbuntu Log Grabber from the menu, and it showed an empty file.  Weird.  I then ran it manually from a Terminal window and got an error.  I wondered about file and directory permissions but as far as I can tell they look fine.  I then ran the Mythbuntu Log Grabber as super-user, and it worked.  I didn't learn anything about what's going on from there, or in any of the logs in /var/log/.  I did notice however that there were other log files empty and not getting filled.  On the other hand most of the log files are are being filled as usual.

By the way, I tried loading the old 2.6.28-15 kernel via Grub, but the results are exactly the same.  No network, and odd behavior w/respect to log files.  I'm stumped.  I've looked and looked and can't find any description of similar problems anywhere.  The only things I did were the radeonhd driver update mentioned above, and I followed those instructions exactly, and then upgraded to the new kernel, and then lastly deleted the cache directory.  I don't which of those got me into my current pickle.  I do know that the network was still working after the radeonhd upgrade since I was able to upgrade the kernel through update manager afterwards.  I also don't know at which step the log writing problem kicked in.  Any suggestions on how I can troubleshoot either of these issues would be greatly appreciated.

---

### Post by inovermyhead on 2009-10-30
Well this may or may not be relevant.  It appears after further and more cautious reading that perhaps instead of deleting the entire ~/.cache directory I should perhaps only have deleted the ~/.cache/sessions directory and that might have sufficed to cure the desktop problem I had.  That may have been what led to my other problems.  Or not.

---

### Post by inovermyhead on 2009-10-31
Hmm, response is less than overwhelming.  Is there a better sub-forum to have posted this in?  Open to any and all suggestions.

---

### Post by inovermyhead on 2009-11-01
How can I get this post moved to the "Networking and Wireless" sub-forum?  I'm thinking I may have better luck there, but didn't want to cross post.

---

### Post by inovermyhead on 2009-11-04
I moved my questions over to the Networking and Wireless forum.  This thread can be killed if necessary, and if there's a moderator about with the power.

---

