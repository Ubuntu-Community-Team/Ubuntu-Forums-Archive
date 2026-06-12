---
title: "linksys WMP300N on Ubuntu 10.04"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by DeltaFee on 2010-04-30
Hey everyone I am quite confused on how to get this thing working I was wondering if anyone know how to configure it.

---

### Post by DeltaFee on 2010-05-01
Okay so I followed this walk through in getting the driver to work:
[http://atpeaz.placidthoughts.com/index.php?/archives/312-Fix-Getting-Linksys-WMP300N-to-work-on-Ubuntu-8.10.html](http://atpeaz.placidthoughts.com/index.php?/archives/312-Fix-Getting-Linksys-WMP300N-to-work-on-Ubuntu-8.10.html)

but for some strange reason I am still not getting it to work.

---

### Post by Blaze247 on 2010-05-11
Hello, I registered just to leave this message for fellow users of the Linksys WMP300N hardware (I found these forums very useful in the past).  I noticed the hardware-drivers application automatically detected a broadcom driver was needed for the wireless adapter.  This works but unfortunately it doesn't stay at a stable speed and drops to 2 mb/s when it should be in the wireless N speeds.

The solution:

Install the windows wireless driver installation GUI for ndiswrapper.  You can find it in the ubuntu software center.

Once installed open it and click add new driver.

Now you'll need the official driver from your linksys cd that came with your hardware.

Browse to the bcwml5.inf file in the /drivers/ folder on the Linksys CD.

That's it! I think you'll have to disconnect and reconnect from your network manager or reboot to get it to switch from the recommended driver wl to ndiswrapper.

My speeds went from 2 mb/s to 130 mb/s  HUGE difference. 

Anyway hope this helps, worked for me on Ubuntu 10.04 Lucid. 

-My 2 cents back to the community.  \\:D/

---

### Post by A4orce84 on 2010-05-17
anyone else success with using windows driver?

Blaze -- can you post up a step-by-step guide?

---

### Post by Blaze247 on 2010-05-18
I'm reluctant to go into to0 many details with this as I have no idea what kind of problems it could cause.  I noticed this wasn't 100% stable either. I had random drops or complete loss in connectivity. But I did notice a huge difference.

1.Open Ubuntu Software Center
2. in the search box type: wireless
3. select the Fifth application down the list titled "windows wireless drivers"  (you can find more info on this project here: [http://jak-linux.org/projects/ndisgtk/](http://jak-linux.org/projects/ndisgtk/) )
4. Click install it should ask you for password.
5. open your gnome menu browse -> administration  then open-> windows wireless Drivers
6. Put your linksys driver Cd that came with your wireless hardware into the cd tray.
7. in the windows wireless Drivers GUI select "install new driver"  
8.  Browse to the bcmwl5.inf file in the cdrom0/Drivers/ folder on the cd you just placed in your computer. 

Thats almost it just select Install.

The last final step is switching from the wl driver to the ndiswrapper.  I havent figured out what the terminal command to do this is or an exact method for this just make sure you've uninstalled all wireless hardware drivers from your admin->hardware drivers menu, aside from the b43fwcutter (I dont know if it makes a difference im no expert).  If you dont have b43fwcutter you can get it through the synaptic package manager by searching: broadcom. 
or to install b43fwcutter
```
sudo apt-get install b43-fwcutter
```

The best method I found was restarting the machine.  After boot right click on your wireless icon in your gnome bar, then click connection information.  You should see next to "driver:" ndiswrapper.  If it still says wl then you may have to blacklist the driver.

to blacklist the wl driver if need be open a terminal and type: 
```
sudo gedit /etc/modprobe.d/blacklist
```
then in the text editor that opens type on one line:
```
blacklist wl
```

For me this worked, I have 130 mb/s connection as opposed to the 2mb/s on default install. I can't garuntee its perfect, I noticed a few odd bugs on boot but they clear away if you give it a minute to connect to your router before clicking anything.  Cheers hope this helps.

edit: Here's a topic detailing the bugs I experienced as well as the solutions.  Dont be discouraged if it disconnects randomly and refuses to reconnect. I believe this person solved that problem. [http://ubuntuforums.org/showthread.php?t=603437](http://ubuntuforums.org/showthread.php?t=603437)

---

### Post by Blaze247 on 2010-05-18
While my advice will work, I noticed that b43 fwcutter had issues while upgrading from karmic to lucid on another computer of mine.  If the method above fails simply uninstall all the broadcom drivers as well as the windows driver installer.  Simply reinstall the STA broadcom driver from your hardware drivers menu with your ubuntu live cd in the cd tray along with the CD source enabled in your software sources.  This should help people who have no internet connection and find the nsdiswrapper driver too buggy.

If you just want it to work and dont care about speed the STA broadcom driver will work fine.

---

