---
title: "iwlist without sudo"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by lvleph on 2009-02-26
I am trying to write a perl script that will execute a particular command if it see a particular ESSID. I decided the command 
```
iwlist wlan0 scan essid NNN
``` would work best. However, this command requires sudo to work correctly. Well that is my problem. How am I going to run this script using cron if I need sudo? Any ideas?

Sorry if this is in the wrong section; it is one of those questions that are hard to place correctly.

EDIT: I solve my own issue by using the following:
```
echo password | sudo -S iwlist wlan0 scan essid NNN
```

---

### Post by nixscripter on 2009-02-27
An alternative might be to make the script set-UID root, which would always run it as root, and then drop its own permissions after the command has executed. If you do this, make sure to run it with the -T option in Perl (on the shebang line of the script).

---

### Post by geirha on 2009-02-27
A third way is to allow your user to run iwlist with sudo, without requiring a password. You do that by running ```
sudo visudo
``` Now, first off, doing a mistake in this file and saving it, may make you unable to use sudo, so to be on the safe side, also open another terminal where you run "sudo -i" to get a root shell. Keep that window open until you have checked that sudo works as normal afterwards. If sudo does not work afterwards, run visudo in the terminal you got the root shell and revert the change.

In the sudoers file, which the visudo command opens for you, you'll see a line at the bottom that goes:
```
%admin ALL=(ALL) ALL
```
which means that all members of the admin group are allowed to use sudo on any command (but must provide password).

Underneath that line, add the following line
```
*yourusername* ALL=NOPASSWD: /sbin/iwlist
```
And save. After that, the user *yourusername* should be able to run ```
sudo iwlist ...
``` without providing a password. 

Better than having the password in clear text in a script in my opinion.

---

### Post by lvleph on 2009-02-27
Yeah, I found those no password options, but there is something I just don't like about it. Anyway, thanks for the ideas.

---

