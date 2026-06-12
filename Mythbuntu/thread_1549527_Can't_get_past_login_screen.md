---
title: "Can't get past login screen"
date: 2010-08-09
forum: Mythbuntu
---

### Post by itlarson on 2010-08-09
This is kind of a re-post, So hopefully I will be able to present the problem more clearly.

I am trying to repair a mythbox which went down due to a power outage.  When the power came back on it booted normally- to a point.  This box was set for auto-login, but instead of logging in, it stopped at the graphical login screen, the way a computer which was not set up for auto-login would.  When the password was entered, the screen blanked for a second, and then returned to the login screen without further feedback.  Repeated login attempts an reboots give the same result.  It is possible to get a command-line login with ctrl-alt-f1 though.

I found a similar issue in a post on the ubuntu forums at [http://ubuntuforums.org/showthread.php?t=1507373]("http://ubuntuforums.org/showthread.php?t=1507373").  Is this the right solution?  If so how do I  make it work for xfce?  Maybee "sudo apt-get install xfce4-session" would be a good place to start?

---

### Post by itlarson on 2010-08-09
Here's something else I found:

> 
Originally Posted by ivoshm View Post
Try switch to text console (Ctrl+Alt+F1), log in and remove file $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml, log out from text console, switch back to graphical login screen and try login again.

If it helped ... write here [http://bugzilla.xfce.org/show_bug.cgi?id=5932](http://bugzilla.xfce.org/show_bug.cgi?id=5932) "ME TOO" 

it was in the following post:

[http://www.uluga.ubuntuforums.org/showthread.php?p=9693681]("http://www.uluga.ubuntuforums.org/showthread.php?p=9693681")

This seems to be an old xfce bug.  I will try this fix tomorrow unless someone recommends otherwise.

---

### Post by itlarson on 2010-08-10
No one?

I tried removing the xfce config file, but it didn't exist.  

I am now noticing that / is completly full.  Could this cause such a problem?  It is only 10gb, as I was not intending to use it for recordings.  Can someone tell me the default storage locations mythtv uses?  I know some of them are root, and it is possible I forgot to remove them when I did the setup.  

I will try to get the logs tomorrow, but I don't have physical access to the computer right now.

---

### Post by laffinet on 2010-08-10
> **itlarson said:**
> I am now noticing that / is completly full.  Could this cause such a problem?

Most certainly !

> Can someone tell me the default storage locations mythtv uses? I know some of them are root

/var/lib/mythtv

which is under / (root) unless you have a separate partition which is mounted to /var/lib/mythtv

I'd say you need to free up some space on / and then change the storage locations so that / doesn't fill up with recordings and liveTV

---

### Post by itlarson on 2010-08-11
Thanks- I will try this tonight.  If a directory outside of home is being used for storage, it was an oversight on my part.  Does anyone know an easy way to find out what's using harddrive space from the command line?

---

### Post by nickrout on 2010-08-11
> **itlarson said:**
> Thanks- I will try this tonight.  If a directory outside of home is being used for storage, it was an oversight on my part.  Does anyone know an easy way to find out what's using harddrive space from the command line?

cd /
sudo du --max-depth=1|sort -n

---

### Post by itlarson on 2010-08-11
Problem solved!

I was trying to make a dvd from a TV show.  I haven't used mytharchive much, and didn't realize it's working directory is configured in the frontend settings, instead of the storage groups.  The default location is /var/lib/mytharchive.  Since I use a traditional style separate root directory of only 10gb, this resulted in mytharchive completely filling my root partition.

I am wondering if I should file a bug report, or feature request about this.  It seems to me that mythtv should ask which partitions should be used for data storage during setup, or at least check that they are of a reasonable size.  Also, this should really be in storage groups instead of the frontend settings.  

Thanks to everyone for all the help.

---

### Post by nickrout on 2010-08-12
not a bug as such, the mythtbuntu installer is supposed to set up a separate mount point for /var/lib which covers all your data.

---

### Post by itlarson on 2010-08-12
I suppose I could put my storage directories there, but I've always put them in the home directory.  I'm just not crazy about user data being outside of home, and it is usefull to have a large home directory for other data.  It would be nice if there was some checking done by mythtv at install time to see if the directories it uses are suitable.  It once took me two days to get a re-install to record.  The only thing wrong was that user I.D.'s had changed, and my storage directories were now read-only.  It would be easy for the installer to check for this sort of thing, and point it out.

My other issue is that this directory is set in the frontend, not in the storage g roups.  If it was set in storage grou ps I would have noticed the problem at the time I set things up.  It makes much more sense to have this all set up in one location, instead of having to dig through the entire frontend setup menu, looking for potential problems.  I am wondering if this is in the works, since mythtv is moving towards a greater reliance on the storage gro ups.

(P.S. why is "g r o u p s"  a censored word in this forum?)

---

### Post by klc5555 on 2010-08-12
> **itlarson said:**
> 

(P.S. why is "g r o u p s"  a censored word in this forum?)

Looks like "a g e d" is also censored, since it got blooped out of the word "m a n a g e d" in another thread, leaving "man****"

Who knew that forum software was so socially progressive?

---

