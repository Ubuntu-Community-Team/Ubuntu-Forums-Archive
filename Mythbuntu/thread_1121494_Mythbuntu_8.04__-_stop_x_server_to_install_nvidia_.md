---
title: "Mythbuntu 8.04  - stop x server to install nvidia driver"
date: 2009-04-10
forum: Mythbuntu
---

### Post by scootre on 2009-04-10
My Mythbuntu 8.04 system is showing the video driver as nv in xorg.conf

I want to change it to a driver from here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

After downloading the driver with wget and running it, I get a message saying X is already running.

How do I Stop the X server?  I've tried sudo init 1 and then I see the session closing but it then locks up with the Mythbuntu Logo in the middle of the screen and its underlining 'progress bar' at about 95%.

Is there an easier way to stop it?

I've also already tried hitting esc during boot to get to the boot menu.  I can arrow up and down the list but pushing e or c does nothing.

---

### Post by scootre on 2009-04-10
All I want to do is stop the X server - or start with no X server running.  Anyone?

Hell, I'd be happy with knowing what the correct search terms for these forums would be.

---

### Post by scootre on 2009-04-10
Browsing the forums finds this:
[http://ubuntuforums.org/showthread.php?t=813798&highlight=mythbuntu+stop+gdm](http://ubuntuforums.org/showthread.php?t=813798&highlight=mythbuntu+stop+gdm)

But I want to know the right way to do it.

It seems when searching for something related to "X" that the search facility doesn't allow words smaller than 3 chars.  :/

---

### Post by jyavenard on 2009-04-10
do:
Ctrl-Alt-F1 to get type to a text console.
Log in

type:
sudo /etc/init.d/gdm stop

do your thing like upgrading the nvidia drivers 
then:
sudo /etc/init.d/gdm start

to restart X

What don't you use packaged nvidia drivers rather than going through the hassle of running scripts.
If you're after the latest nvidia 180.x drivers, I've made packages for Jaunty .
[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

---

### Post by scootre on 2009-04-10
Hi jyavenard 

> **jyavenard said:**
> do:
Ctrl-Alt-F1 to get type to a text console.
Log in

type:
sudo /etc/init.d/gdm stop

I did that also.  The system would start closing the X server and then freeze.  No idea why.

Anyway, I temporarily removed the reference to gdm in /etc/rc2.d then restarted and then had no X running which is what I wanted.

A long way around unfortunately.

[QUOTE=jyavenard]
What don't you use packaged nvidia drivers rather than going through the hassle of running scripts.
[/QUOTE]

It wasn't really a problem.  Once I was in a console it was wget the package then run the script and it was done in seconds.

Now the 1920x1080 res on my TV looks bloody beautiful.  :)

[QUOTE=jyavenard]
If you're after the latest nvidia 180.x drivers, I've made packages for Jaunty.

[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)
[/QUOTE]

Cool.  I'll definitely bookmark those for next time.  And there'll always be a next ime.  :)

Thanks a lot for your help.

Edit:  Man, you've put some work into your Web Site.  Nice!

---

