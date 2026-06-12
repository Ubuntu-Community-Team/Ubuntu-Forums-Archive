---
title: "Having to manually log into wireless after Hardy install"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by stinkwheel on 2009-01-11
This is a problem with a friends computer which I don't currently have in front of me. She is not very computer literate so I will have to either be able to call her with something very specific to do and talk her through it or wait until I'm round next which will not be for some time.

It is an older Dell Desktop with a 2.40GHz celeron processor and 1Gb of RAM. 

It is currently running Ubuntu 8.04 which was a clean install rather than an upgrade. It is fully updated with all the usual software sources enabled.

It is using a Belkin USB wireless dongle with a Railink RT2500 series chipset.

This machine was previously running Ubuntu 7.10 for 18 months and the wireless was problem free.

I do not have access to the wireless router to alter settings, I can only power cycle it. It is not practical to use my preferred option of using a wired connection (two premesis share the connection, the router is in the building next door).

The other (windows) machine on the router is not experiencing problems.

When I first started the fresh install, network manager came up with the list of networks it detected. I selected the correct one, entered the WEP key and it connected. Since then it has been highly intermittant.

On startup, the computer can see the network and gives every impression of having connected. It can see the router and reports back with a signal strength (showing the "graph" applet, not the "searching" one). However opening a browser just leaves it hanging on "looking up". Update manager and synaptix wont connect.

I initially thought it was a DNS problem but I tried pinging 216.239.59.103 (google) directly and got no response.

Changing to manual configuration, selecting the network SSID from the dropdown menu, typing in the WEP key and selecting Auto DCHP gives me a connection. I don't see why this should be any different to leaving it in roaming mode.

I tried saving the above manual settings as the default location but still have the same problem. It just wont reliably connect on startup unless I physically enter the details under manual confuguration.

I tried re-installing Network manager using synaptix with no effect.

I have showed my friend how to manually connect but she shouldn't really have too and I feel like an idiot for having "broken" her computer.

Something elese I noticed is that it seems to come up with the "connected" network manager applet a LOT more quickly than it did when running Gutsy. It used to sit with the "searching" one for a good 10-15 seconds whereas now it appears to connect almost instantly. 

If anyone has some suggestions for what to try next, I would be grateful.

---

