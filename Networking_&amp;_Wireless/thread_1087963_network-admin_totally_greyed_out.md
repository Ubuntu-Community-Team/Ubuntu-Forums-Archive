---
title: "network-admin totally greyed out"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by John Chambers on 2009-03-05
When I start network admin, either from a menu or from the command line, and even with "sudo network-admin", its window comes up totally greyed out, and nothing works.  The manual says it'll ask me for my password to get admin privileges, but it doesn't do this at all.

The only clue I've seen is that when I start it with sudo, I get:

# network-admin

** (network-admin:26705): CRITICAL **: Cannot create session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(network-admin:26705): Gtk-WARNING **: Unknown property: GtkComboBox.items


** (network-admin:26705): CRITICAL **: Unable to find session for cookie

I've tried searching ubuntuforums for the various strings there, especially "Cannot create session bus", but I get no matches.

Anyone know what might be wrong, or how I might diagnose the problem?

Meanwhile, I'll go back to the CLI, editing config files, and so on, as I've always done before.  But I'd like to learn to use the GUI tools, if I can get them to work.

---

### Post by John Chambers on 2009-03-05
Additional evidence:

After googling for the messages, I found a lot of suggestions that network-admin should be run from my account, or via sudo, or via gksudo, and it would ask for my password.  I tried all three.  Typical was:

$ gksudo network-admin
(network-admin:27773): Gtk-WARNING **: Unknown property: GtkComboBox.items


** (network-admin:27773): CRITICAL **: Unable to lookup session information for process '27773'
$

This doesn't have as many messages as when I ran it after using "sudo tcsh" to get the '#' root prompt.  But the above two messages are produced by all of them.

Attempts to diagnose this have led to dead ends so far.  There are lots of suggestions that I should do what I've done, and I'd get the prompt for my password to give network-admin the privileges it needs.  This has never happened; I get the above error messages simultaneously with a window opening whose title bar identifies it as "Network Settings", and everything except the Help and Close buttons are greyed out. I've had the Help window open for some time, but it doesn't seem to deal with this problem. The Close button works just fine. ;-)

---

### Post by jimishol on 2009-06-14
After upgraded from Gutsy to Hardy i had the same problem. Due to some search i checked /etc/hosts and /etc/hostname and noticed that in hostname the computer's usual name was modified as usualname.SIEMENS I don't know how it did happened but i think that that name apperared in network-admin window too. I added after a blank space the usualname and dont remeber if i modified hosts too. Nothing changed and decided to install network-config and for days i activated my network from there. I need to do it after every reboot due to some problems with my routers. That was annoying and today i decided to remove gksu from the command that was running the network-admin through menu configuration. At once my problem was SOLVED.
It seems that from command line the command network-admin would be enough. I hardly believe i didnt that in past but today i surely did.
I changed my computers name from there from usualname.SIEMENS to usualname or the opposite (sorry i dont remeber) and rebooted but gdm wouldnt start. From grub i entered in command line and modified hostname.
After loggining in i made sure that hostname and networkadmin have no SIEMENS and all now seems back to normal if not better.

---

