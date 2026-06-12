---
title: "Ath5k Wireless Driver WPA2 Enterprise Connection Issue"
date: 2013-03-20
forum: Networking &amp; Wireless
---

### Post by nbpradford on 2013-03-20
Let me outline my situation for you, an old Macbook 13" (1.1), running Ubuntu 12.04.  I have a AR242x / AR542x wireless interface currently using the ath5k wireless driver.  On my schools secure wireless they secure it with a WPA2 Enterprise with PEAP and MSCHAPv2 authentication.  I can connect to any AP and get on the internet, but I can only connect a certain distance from the AP.  If I move away/closer from said AP I may maintain connection, but there is also a chance I will drop the signal and return to having to authenticate my computer again.  Again this repeats the process of the interface having to be within a certain distance of the AP and sometimes wont be able to connect at that distance.  After comparing notes with my schools IT we noticed my computer would connect within a certain distance of the wireless AP and then once the distance would change the computer was having trouble staying connected.  If I understood my schools IT right it was the process of elevating from lets say A to G that would boot the computer off the network and require it to re-authenticate.  I didn't know if this was a driver issue?  And that if I change my wireless interface driver from the ath5k driver to the MADWIFI driver would I not have these connection issues on my schools network.

I also may believe this is a distance issue with the driver itself in a WPA2 Enterprise PEAP, MSCHAPv2 secured network, but I haven't been able to test this idea.

I have an idea of what I'm doing on linux, and I'm willing to try anything so any kind of suggestion will work.  And yes I've Googled this, and searched the forums; extensively.  

[B]TL;DR: AR242x / AR542x wireless interface using ath5k drivers.  Has connection issues with schools secure wireless network.  The network uses a WPA2 Enterprise, PEAP, MSCHAPv2 authentication.  Interface struggles to connect and is very temperamental based on distance to the access point.  Should I switch to the madwifi driver or are there other alternative fixes to this issue?
[/B]

---

### Post by wildmanne39 on 2013-03-20
Hi, please try:
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k

```
Thanks

---

### Post by nbpradford on 2013-03-21
Thanks Wild Man for the quick reply,
The code helped, but didn't fully fix the issue.  It definitely helps improve the connection overall.  One thing i'm noticing is when I believe i'm getting maximum range of the AP and my interface disconnects, my interface struggles to reconnect to the next closest AP, i believe it continues to try to reconnect with that last AP.  

Now I appreciate your help, but can you explain what this just did?  I like making things work, but I also like understanding why it works.

Thanks again!

---

### Post by wildmanne39 on 2013-03-21
Hi, we changed encryption from hardware to software that usually makes the connection a lot more stable including reaching a little further.

I am working right now just taking a few mintues break please post by, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by nbpradford on 2013-03-26
The file size exceeded the forums limit so here is a link to the netinfo file.

Thanks again for your help,
things are looking a lot better but as you can see from the error messages at the bottom of the netinfo there's still some issues going on.

---

