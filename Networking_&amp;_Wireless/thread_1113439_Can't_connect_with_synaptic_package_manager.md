---
title: "Can't connect with synaptic package manager"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by jonwh25 on 2009-04-01
This is a pretty strange thing I'm encountering. Let me give a brief background on this first.

I just installed a fresh copy of 8.10 on my laptop. I installed this at work and set everything up to point at our network proxy server. No big deal everything ran fine.

Now when I bring up my laptop at home and try to run the synaptic package manager to install a few things or even use the update manager it comes back with 

```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/r/resolvconf/resolvconf_1.42ubuntu2_all.deb
  Could not resolve 'proxy-server'

```

Yes, I knew to go in after I booted up my laptop at home to go into System->preferences->Network Proxy and change the manual proxy configuration to "Direct internet connection" and then apply system wide. This was done BEFORE I tried to go and install new packages. 

I googled around and came across trying to use unset http-proxy from the command line terminal and then I ran sudo apt-get update and it looked like it connected just fine....

I went back into the synaptic package manager and got the SAME error. I went to command line and ran the command sudo apt-get install wifi-radar and it pulled it and installed it.

So it looks like the GUI front ends are broken?? or perhaps I'm missing something. I checked my /etc/apt/apt.conf and the file has nothing in it. 

Can anyone shed some light on this?

---

### Post by jonwh25 on 2009-04-01
Hrm. Searching this forum I found a similar thread. I went into the synaptic package manager. Then I selected settings->preferences and then clicked the network tab. It "appeared" it was ok said direct connection but I went and clicked proxy, filled out the settings for work, clicked apply then checked direct connection and clicked apply and it fixed it. This looks like a bug that hasn't been fixed. I'm hoping the fix is included for 9.10...

However I still can't use the "update manager" tool. When I try to "check" for new packages it gives me the failure for proxy... strange things...

---

