---
title: "Manual IPv6 Address Configuration Doesn't Work"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by trellis3 on 2010-01-16
After discovering this doesn't work on Fedora, I thought I'd give Ubuntu a try, and unfortunately it doesn't work on Ubuntu either. Worse, attempting to do it completely breaks IPv6 networking. 

You can set the Method to "Manual" and then enter the IPv6 address and prefix you wish to use. Clicking "Apply" then causes all networking (IPv4 and IPv6) to go down, so you right-click the network icon at the top of the screen, disable networking, the enable it again. This brings back IPv4, but IPv6 is now only using link-local addressing. If you go back into the IPv6 settings, it's remembered that you wanted "manual" addressing (which is more than Fedora does!) but it seems to have forgotten the configured IPv6 address. 

Once this has happened, I can't find any way to re-enable stateless autoconfig and get IPv6 connectivity back, but that's a side issue. What I really need to be able to do is manually configure the IPv6 address. 

Is there any chance this will be fixed, or do I need to keep trying different Linux distros until I find one that works? 

I'm afraid Microsoft are way ahead here - Vista had manual IPv6 config support, and it worked perfectly, as I'm sure it does on Windows 7.

---

