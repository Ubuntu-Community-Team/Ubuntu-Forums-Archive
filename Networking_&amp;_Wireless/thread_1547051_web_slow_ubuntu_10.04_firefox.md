---
title: "web slow ubuntu 10.04 firefox"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by aidanewen on 2010-08-06
I've got my desktop PC set up to dual boot windows 7 and ubuntu 10.04. I use firefox as my browser on each operating system but for some reason the windows machine loads web pages much faster. It can take my ubuntu machine 20 seconds to load a basic web page (that would take the windows machine <3 seconds). It's a bit frustrating as I'm using the ubuntu side more and more for development. I've also got a couple of Mac's in the office that seem to have the same problem - intermittently slow browsers (when everyone else is running fine).

I've got a small private wired network (maybe 15 IP's), with these machines on DHCP, NATing out through a draytek vigor 2820 router onto an ADSL line (with a download speed of about 13Mb).

I can't work out why this is happening and I don't really know where to start, but I'd love to get it sorted.

Any ideas?

---

### Post by aidanewen on 2010-08-06
Looks like firefox is the issue. I noticed it stalling while displaying a "looking up ......." in the bottom left corner, and found a few people on other forums discussing the issue. Google chrome seems to be the solution for me (web access is fine now).

---

### Post by texla on 2010-08-06
Usually in Firefox, you need to do the following:
Open your Firefox browser, and in the field where you would normally  type a web address (like [http://www.ubuntu.com]("http://www.ubuntu.com/")),  type

**about:config**

It'll display a warning about messing around with the configuration.   Answer by clicking on the button that says, "I'll be carefull, I   promise!"

Now scroll down that list of settings until you find the one that says, 

"network.dns.disableIPv6 = false" and just double click on that line. It  will darken and then read,

"**network.dns.disableIPv6 = true.**"

Do the same thing on the lines that say

"network.http.pipelining = false" and
"network.http.proxy.pipelining = false."

That will convert those settings to "true."

Then lastly, find the line that says

"network.http.pipelining.maxrequest" and set that number to 8.

Good luck! - try it you might like it...

---

### Post by aidanewen on 2010-08-06
network.http.pipelining and network.http.proxy.pipelining were already set to false (and changing the network.http.pipelining.maxrequest figure to 8 doesn't make sense if we're disabling pipelining - I did it anyway though). I've disabled the ipv6 dns stuff as you suggested and that seems to have done the trick. Thanks for you're help texla!

---

### Post by texla on 2010-08-06
Glad it worked!  I'm no expert in ubuntu but this trick is something I found on the forum a while back and it's helped a few others so I thought I'd send it your way.  

You might also want to look into ff 4.0 beta if you haven't already.  It's a little tricky to install (there's a lot of  help on the forums about it though) but it seems to be pretty stable for me - still added those fixes above to it however...

---

### Post by Maximus_ARNP on 2010-08-14
These tricks alone did not speed up my Firefox on Ubuntu 10.04. I had to deploy **all additional tips and tricks (including creating all new integers, fixing memory leaks by using 32MB) offered at following link:**

[**http://www.ubuntugeek.com/speed-up-firefox-web-browser.html**]("http://www.ubuntugeek.com/speed-up-firefox-web-browser.html")

After setting things as indicated above, I cleared all browsing history, forms, and passwords.

After restarting the Firefox, it was **blazing fast.**

Enjoy.

---

### Post by barney385 on 2010-09-07
I downloaded and installed 4.0 but it's not showing up as a browser option.

Do I have to start the app from terminal?

---

### Post by texla on 2010-09-08
Try unpacking the folder to home then click on:

 run-mozilla.sh - choose the option to run in terminal.

Then if you want to use it, make a shortcut launcher on you panel with this command:
~/firefox/firefox

with the beta, you will still have an older version of ff installed and you can see it in your internet shortcuts.  Then if updates mess it up (which they always do), you can go back to the older version while you figure it out - the one consolation is it does seem to remember your bookmarks from the beta somehow....

---

### Post by elico on 2010-09-08
remove firefox completely and reinstall it?
if it's working on chrome that means that something between your os and FIREFOX is not fine.
did you ever tried to ping google?

> ping [www.gooogle.com](www.gooogle.com)
or
> dig [www.google.com](www.google.com) 

---

### Post by truenite on 2010-10-25
Texla Thank you alot!! This really helped!!!

---

