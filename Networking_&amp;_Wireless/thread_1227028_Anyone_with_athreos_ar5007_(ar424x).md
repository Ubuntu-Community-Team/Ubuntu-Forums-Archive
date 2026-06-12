---
title: "Anyone with athreos ar5007 (ar424x)"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by davewickett on 2009-07-30
ANYONE WITH ATHREOS AR5007 (AR424X) IN UBUNTU AND NEED TO GET WORKING IN UBUNTU JUST COPY & PASTE THIS INTO YOUR TERMINAL I HAD THE SAME PROBLEM AND THIS AS WORKRD FOR ME AND ITS BEEN FINE AND IT WORKS WITH AIRODUMP & KISMET AND STUFF SO GOOD LUCK HOPE IT WORKS AND HELPS OTHER PEOPLE OUT I THINK WHEN I DOWNLOADED THE CODE I COPYED & PASTED IT IN THE TERMINAL TO DOWNLOAD IT AS WELL 

Install Atheros AR242x 802.11abg Wireless Driver in Ubuntu
Tagged:  

    * Drivers
    * Hardware
    * Ubuntu 8.10
    * Ubuntu 9.04
    * Wireless Drivers

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

    * Reboot. It should work now. 

DAVE :biggrin::biggrin::biggrin:

---

### Post by davewickett on 2009-07-30
FOR PEOPLE WHO HAVE DONE THIS FROM MY POST TO GET WIFI WORKING WHEN YOU UPDATE KERNEL IN UBUNTU YOUR WIFI WILL NOT WORK ANYMORE AND YOU WILL HAVE TO COMPILE IT WITH YOUR NEW KERNEL TO DO THIS 

  i have to cd back in madwifi sorces dir launch a make clean && make && make install , and then i will have my wireless devices up again



First I rebuilt the atheros driver. If you followed my intructions above then at the terminal prompt you can change into the driver directory like this:

Code:

cd ~/madwifi/madwifi-hal-0.10.5.6

Then clean out old make settings so it will be built to match the new kernel:

Code:

make clean

Build the driver

Code:

make

I don't know if it's necessary but this might be a good place to remove the old driver from the running kernel:

Code:

sudo modprobe -r ath_pci

Now install the driver:

Code:

sudo make install

I tried reloading the ath_pci module with modprobe but it still wouldn't work. I think a reboot is necessary at this point.

It should work now after a reboot. Good luck.

DAVE:D:D:D

---

