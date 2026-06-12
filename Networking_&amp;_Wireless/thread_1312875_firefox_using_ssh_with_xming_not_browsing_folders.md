---
title: "firefox using ssh with xming not browsing folders"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by grizzlylock on 2009-11-03
Sorry if I shouldn't start a new thread but I didn't find anyone else with the same issue.

I set up a hardy linux box to use for secure banking at my agency.  I use xming as the xwindows system on the windows pc and use putty to ssh into the linux box.  The issue is that firefox opens but the folder browser used to upload files does not work properly.  It usually just hangs without showing the folders (even local folders since I have windows shares mounted via cifs).  It seems to be specific to firefox because I loaded ie4linux and it browsed fine but hangs too much to be applicable for this situation.

Any ideas?

---

### Post by grizzlylock on 2009-11-05
Apparently this must just be due to firefox just being very sluggish.  I've installed the latest chromium build and it browses folders great but it doesn't have ie tab extensions for the bank page.  Anyone manage to get Chromeplus to work with wine?  Chromeplus has the ietab addon.

---

### Post by grizzlylock on 2009-11-09
Is this in the wrong category?  I've been reading these forums for quite some time and it seems that people always get at least some response relatively quickly.  If this is posted in the wrong area can someone please direct me to the right category to receive some assistance?


Here is the scenario... and any suggestions on a different way to do this would be equally welcomed.

I've set up a linux box with hardy on it for users to use for accessing the bank website.

What I've done is used the ssh protocol to remote into the linux box to access the banking website remotely from their computer but through a secure channel on a secured box.

I used xming as the xwindows program on windows and firefox with ie addon on ubuntu to access the webpage via ssh.

The problem seems to be that firefox doesn't work when attempting to upload files from a network share (or locally from the linux box) to the webpage.

The 'open files' browser hangs or even doesn't show the folders when it comes up.

With the network shares I used the cifs protocol to map the windows shares to the profiles.  And I don't know if this is of any relevance but I've added the linux box to the domain using likewise-open and thus it authenticates with the active directory.


Please if anyone can help me it would be much appreciated.  I have confidence in you!  I've been reading these forums since I started using linux and there are some smart folks on here.  And yes I am trying to butter you up! ;)


Thanks,
Steve

---

### Post by grizzlylock on 2009-12-01
As an update and maybe a death of this project, here is where its at.

I gave up on firefox!  There just wasn't any way to get it working well.

I decided to try chromium as I had said before.  There was no ie pluggin but you can call chromium with a user-agent option that allows you to mask chromium as ie.  This is the command I used.

chromium-browser --user-agent="Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0)"

This allowed me to access the bank website as well as upload files correctly.  However, the bank website did not load entirely properly so it was unusable by the finance department. :(

That was the end of my tunnelling endeavors!  I simply need ie!

So I configured the server to act as a firewall for a socks5 protocol.  That doesn't seem to add the level of security that I was looking for...i.e. it won't protect from keystroke recording maleware.  Thus I will impliment nothing and just watch those computers like a hawk.

It was an informative project though :)

If anyone wants to know more about how to impliment a similar setup drop a line.  Chromium might just work for you...and firefox for that matter if you don't need to upload files.

---

