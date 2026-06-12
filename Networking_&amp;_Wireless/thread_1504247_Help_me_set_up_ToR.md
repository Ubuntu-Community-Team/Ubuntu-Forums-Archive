---
title: "Help me set up ToR :/"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by drackor1991 on 2010-06-07
Help with setting up ToR. I think I've gotten as far as 

"
After installing Tor, you need to configure your applications to use  it. 
  The first step is to set up web browsing. Start by installing [Polipo]("http://www.pps.jussieu.fr/%7Ejch/software/polipo/") from your favorite repository. Polipo is a caching web proxy that does http pipelining well, so it's well-suited for Tor's latencies. Make sure to get at least Polipo 1.0.4, since earlier versions lack the SOCKS  support required to use Polipo with Tor. You should uninstall privoxy at this point (e.g. apt-get remove privoxy or yum remove privoxy), so they don't conflict. 
 Once you've installed Polipo (either from package or from source), **you will need to configure Polipo to use Tor**. Grab our [Polipo configuration  for Tor]("https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf") and put it in place of your current polipo config file (e.g. /etc/polipo/config or ~/.polipo). You'll need to restart Polipo for the changes to take effect. For example:
/etc/init.d/polipo restart 
 If you prefer, you can instead use Privoxy with [this sample  Privoxy configuration]("https://wiki.torproject.org/noreply/TheOnionRouter/PrivoxyConfig"). But since the config files both use port 8118, you shouldn't run both Polipo and Privoxy at the same time."
But dont know how to replace that config file or w/e. Please halp.

---

### Post by SlidingHorn on 2010-06-07
> **drackor1991 said:**
> Help with setting up ToR. I think I've gotten as far as 

"
After installing Tor, you need to configure your applications to use  it. 
  The first step is to set up web browsing. Start by installing [Polipo]("http://www.pps.jussieu.fr/%7Ejch/software/polipo/") from your favorite repository. Polipo is a caching web proxy that does http pipelining well, so it's well-suited for Tor's latencies. Make sure to get at least Polipo 1.0.4, since earlier versions lack the SOCKS  support required to use Polipo with Tor. You should uninstall privoxy at this point (e.g. apt-get remove privoxy or yum remove privoxy), so they don't conflict. 
 Once you've installed Polipo (either from package or from source), **you will need to configure Polipo to use Tor**. Grab our [Polipo configuration  for Tor]("https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf") and put it in place of your current polipo config file (e.g. /etc/polipo/config or ~/.polipo). You'll need to restart Polipo for the changes to take effect. For example:
/etc/init.d/polipo restart 
 If you prefer, you can instead use Privoxy with [this sample  Privoxy configuration]("https://wiki.torproject.org/noreply/TheOnionRouter/PrivoxyConfig"). But since the config files both use port 8118, you shouldn't run both Polipo and Privoxy at the same time."
But dont know how to replace that config file or w/e. Please halp.

First, you should backup your original config file:

```
sudo cp /etc/polipo/config /etc/polipo/config.bak
```

Then replace the original with the file they gave you:

```
sudo cp /path/to/file /etc/polipo/config
```

As it said...make sure you're not running polipo/privoxy @ the same time.  Hope this helps! :)

---

### Post by drackor1991 on 2010-06-07
> **SlidingHorn said:**
> First, you should backup your original config file:

```
sudo cp /etc/polipo/config /etc/polipo/config.bak
```Then replace the original with the file they gave you:

```
sudo cp /path/to/file /etc/polipo/config
```As it said...make sure you're not running polipo/privoxy @ the same time.  Hope this helps! :)

How do I check if it's running? (linux newbie)

---

### Post by drackor1991 on 2010-06-07
Uh...well. I think I did it....but I put torbutton on firefox and when I enable it I cant go anywhere...and Idk how do get a GUI to change ToRs ip etc...used to windows <.<

---

### Post by SlidingHorn on 2010-06-07
> **drackor1991 said:**
> Uh...well. I think I did it....but I put torbutton on firefox and when I enable it I cant go anywhere...and Idk how do get a GUI to change ToRs ip etc...used to windows <.<

Does it say it's refusing connections?  Try restarting and see if it works (not a canned response...saw someone w/ that problem [here]("http://ubuntuforums.org/showpost.php?p=9338712&postcount=4"))

When it comes to the GUI, have you looked @ Vidalia? [http://www.ubuntu-unleashed.com/2007/09/setup-vidalia-tor-gui-with-ubuntu-and.html](http://www.ubuntu-unleashed.com/2007/09/setup-vidalia-tor-gui-with-ubuntu-and.html)

---

### Post by drackor1991 on 2010-06-07
> **SlidingHorn said:**
> Does it say it's refusing connections?  Try restarting and see if it works (not a canned response...saw someone w/ that problem [here]("http://ubuntuforums.org/showpost.php?p=9338712&postcount=4"))

When it comes to the GUI, have you looked @ Vidalia? [http://www.ubuntu-unleashed.com/2007/09/setup-vidalia-tor-gui-with-ubuntu-and.html](http://www.ubuntu-unleashed.com/2007/09/setup-vidalia-tor-gui-with-ubuntu-and.html)
thats the problem Im having (restarting didnt help)

---

### Post by SlidingHorn on 2010-06-07
If you aren't running Vidalia (that's the GUI that controls tor), go to a terminal:

```
sudo apt-get install vidalia
```

I believe after installation it will show in your menu under Internet.  That will allow you to control ToR and make it run.  Firefox will say that when either ToR's not running or if the settings are incorrect...let me know what you come up with

---

### Post by drackor1991 on 2010-06-07
> **SlidingHorn said:**
> If you aren't running Vidalia (that's the GUI that controls tor), go to a terminal:

```
sudo apt-get install vidalia
```I believe after installation it will show in your menu under Internet.  That will allow you to control ToR and make it run.  Firefox will say that when either ToR's not running or if the settings are incorrect...let me know what you come up with
I have vidalia 

This is what I get if I try to go to a site:
Firefox is configured to use a proxy server that is refusing connections.


And when I test ToR with the firefox button:

Local HTTP Proxy is unreachable. Is Polipo running properly?

---

### Post by SlidingHorn on 2010-06-07
Ran across a couple similar issues searching google...read this one first:

[http://forums.opensuse.org/get-help-here/install-boot-login/427005-how-make-polipo-start-bootup.html](http://forums.opensuse.org/get-help-here/install-boot-login/427005-how-make-polipo-start-bootup.html)

and it will refer to this one @ the end: [http://forums.opensuse.org/get-help-here/network-internet/429127-tor-not-starting.html#post2091241](http://forums.opensuse.org/get-help-here/network-internet/429127-tor-not-starting.html#post2091241)

---

### Post by drackor1991 on 2010-06-07
> **SlidingHorn said:**
> Ran across a couple similar issues searching google...read this one first:

[http://forums.opensuse.org/get-help-here/install-boot-login/427005-how-make-polipo-start-bootup.html](http://forums.opensuse.org/get-help-here/install-boot-login/427005-how-make-polipo-start-bootup.html)

and it will refer to this one @ the end: [http://forums.opensuse.org/get-help-here/network-internet/429127-tor-not-starting.html#post2091241](http://forums.opensuse.org/get-help-here/network-internet/429127-tor-not-starting.html#post2091241)

MY
RunAsDaemon 1

ControlPort 9051
are commented out but I dont know how to change them (have to be root) what sudo command would be used?

---

### Post by SlidingHorn on 2010-06-07
First, make a backup of the file:

```
sudo cp /path/to/torrc /path/to/torrc.bak
```

then, edit the original:

```
sudo gedit /path/to/torrc
```

---

### Post by drackor1991 on 2010-06-07
I just fixed those two things....still not working

---

