---
title: "Not Able To Connect To Internet...  Please Help"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by Thatguy09 on 2009-12-25
Using Ubuntu version 9.04. Works fine on my computer... With company permission I brought into work and tried the demo version on their computer. Everything works fine except I can't browse the net. Says it is connected..  Just times out when I do a search or try to visit a specific web site. Using a wired router with dynamic ip. I'd like to be able to figure out asap a fix for this network issue. I am a linux noob and would appreciate any advice. Thanks.

---

### Post by chewearn on 2009-12-25
About that "wired router with dynamic ip", is it a router connected directly to the internet by some ISP, or is it connected to the corporate network?  Is there a proxy server setting that need to be configured?

---

### Post by Thatguy09 on 2009-12-25
Yes it is a router connected to a corporate network.  Yes there are proxy server settings that need to be configured but unsure how with ubuntu 9.04.  I do not work in the network department.  I was just given permission by them to try the demo on my work PC.  Thank you for responding.

---

### Post by chewearn on 2009-12-25
The proxy settings can be entered at:

Top Menu > System > Preferences > Network Proxy

---

### Post by Thatguy09 on 2009-12-25
I type in the url for the automatic configuration script and still doesn't work.  I try a search on google and it will fill the orange progress bar halfway then stop.  Any other ideas?

---

### Post by chewearn on 2009-12-25
Here are a few ideas:

1. You have to close the browser and reopen it for the proxy changes to take effect.

2. Look under Firefox preferences > Advanced > Network tab > Connection settings; make sure "Use system proxy settings" is selected.

3. Alternatively, you could also try entering the proxy settings directly into Firefox

4. Try manual setting instead of automatic proxy configuration.  For this to work, you need to find out the direct url of the proxy.  You can actually grab the automatic configuration file from it's url.  It's a text file that you could open and read to try figure out the actual url or ip of the proxy.

---

