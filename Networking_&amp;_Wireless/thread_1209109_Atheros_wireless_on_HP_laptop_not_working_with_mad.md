---
title: "Atheros wireless on HP laptop not working with madwifi"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by B_Master_Flash on 2009-07-09
I've searched and read all the related threads I could find but I still can't get my wireless card working.

I've got an HP G60-235dx with an Atheros AR242x PCI Express wireless card, and I'm using the most recent version of Ubuntu (downloaded it last week).  After a little reading I figured out that linux doesn't come with a driver to support this card so you've got to use madwifi.  I found [this website]("http://www.stchman.com/ath_drv.html") that has a script to install madwifi, so I downloaded and ran it.  It completed with no errors, but my wireless still isn't coming on.  Sorry for the possible repost, but any help would be appreciated.

---

### Post by Gripitoy on 2009-07-09
hi, i had the same problem with yours, i installed ubuntu 9.04 (fresh install) then i dual booted it with windows, on my linux install, i activated mad wifi as driver, but when i tried to connect to the internet, it does'nt detect any connection at all, now i tried to deactivate it, restarted my notebook, and voila, it detecting many connections, much more than my windows does..\

so, try to disable first your mad wifi, and reboot, by the way, we have the same wireless hardware...

---

### Post by B_Master_Flash on 2009-07-10
> **Gripitoy said:**
> hi, i had the same problem with yours, i installed ubuntu 9.04 (fresh install) then i dual booted it with windows, on my linux install, i activated mad wifi as driver, but when i tried to connect to the internet, it does'nt detect any connection at all, now i tried to deactivate it, restarted my notebook, and voila, it detecting many connections, much more than my windows does..\

so, try to disable first your mad wifi, and reboot, by the way, we have the same wireless hardware...

Cool thanks for the help.  What do you mean by "disable" the madwifi? Should I uninstall it or is there a way to just turn it off?

---

### Post by Gripitoy on 2009-07-20
> **B_Master_Flash said:**
> Cool thanks for the help.  What do you mean by "disable" the madwifi? Should I uninstall it or is there a way to just turn it off?

there's a way to disable it.. system>administration>driver

---

### Post by davewickett on 2009-07-22
> **B_Master_Flash said:**
> I've searched and read all the related threads I could find but I still can't get my wireless card working.

I've got an HP G60-235dx with an Atheros AR242x PCI Express wireless card, and I'm using the most recent version of Ubuntu (downloaded it last week).  After a little reading I figured out that linux doesn't come with a driver to support this card so you've got to use madwifi.  I found [this website]("http://www.stchman.com/ath_drv.html") that has a script to install madwifi, so I downloaded and ran it.  It completed with no errors, but my wireless still isn't coming on.  Sorry for the possible repost, but any help would be appreciated.
ok u have the same wifi card as me i was trying to get it to work for about 3 weeks day and night and i come across this 


Install Atheros AR242x 802.11abg Wireless Driver in Ubuntu
Tagged:  

    * Drivers
    * Hardware
    * Ubuntu 8.10
    * Ubuntu 9.04
    * Wireless Drivers

I had a chance to install Ubuntu 9.04 in an ASUS EEE PC for a friend of mine. Everything was working smoothly except wireless which was  Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01). Eventhough available drivers were listed on Hardware Driver, it was already in active mode and still not working. Finally i got it working. Here is what i did.

    *  Goto System > Administration > Hardware Drivers and disable both Atheros HAL and the Atheros wireless listed and then reboot.
       
    * Now install build-essential and subversion. Goto Applications > Accessories > Terminal and type as follows.

     sudo apt-get install build-essential subversion

    * Now make a new directory  in you home.

     cd ~
     mkdir madwifi

    * Now cd into the newly created  directory, madwifi.

      cd madwifi

    * Download the code now.            

svn co [https://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6](https://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6)

    * After finishing downloadusing subversion cd into directory madwifi-hal-0.10.5.6

      cd madwifi-hal-0.10.5.6

    * Run make to build the driver.

       make

    * Install the driver.

        sudo make install

    *  Now you have to add the Atheros kernel module to the list of modules to be automatically loaded at boot by adding " ath_pci " (without the quotes) to the end of the /etc/modules file. I used gedit here. You can use the editor of your choice.

        sudo gedit /etc/modules

    * Reboot.

look im new to all this to but lhis got my wifi up and running and its still good now with no problems apart from some of the wifi hacking tools im having a few probs with but this should get up up and running too good luck and let me know how u got on 
dave

---

