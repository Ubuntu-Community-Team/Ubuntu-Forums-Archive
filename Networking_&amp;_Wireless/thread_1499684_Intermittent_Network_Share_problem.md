---
title: "Intermittent Network Share problem"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by Sojurner on 2010-06-02
I have been file sharing across an all *nix (ubuntu 9.10) network and im getting a very annoying problem that i dont know how to fix. I am sharing a couple of folders from an external USB drive. The Share works fine about half of the time.

How i shared it. I just right clicked on the folder and set up sharing from the drop down context menu and was able to view it form my networks menu on my other ubuntu machines.

However about half the time when i select Network from my places menu and i try to go into the "Windows Network" folder which is where it was by default i get this message "Unable to mount locatio: Failed to retreive share list from file server". Sometimes i dont. Sometimes it goes right in and the other half the time i see my other comptuers without ever having to click on the "Windows Network" folder

Please help. I just want this share and the connection to it to be more stable. There are no network issues, i can connect to the internet any time this happens on either computer. Im just really not sure where to even start fixing this.


PS: just as im typing this it all starts working.. i will go out in the next little while though.

---

### Post by mituw16 on 2010-06-02
If i had to guess, the computer that is sharing the folders as an IP that is assigned by DHCP, you should make it static and that usually takes care of most server (including file sharing) problems.

---

