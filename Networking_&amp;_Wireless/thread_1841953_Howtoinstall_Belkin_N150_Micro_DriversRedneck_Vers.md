---
title: "Howto:install Belkin N150 Micro Drivers:Redneck Version"
date: 2011-09-10
forum: Networking &amp; Wireless
---

### Post by Floppyjoe on 2011-09-10
Belkin N150 Micro USB Adapter Installation Redneck Version:for Ubuntu 10.04 LTS Lucid Linx.  Tested on Acer Aspire One Netbook.

> Preamble:The installation probably requires that build-essential and possibly the linux-headers for your kernel be installed on your system.

I would add them by 
a. clicking on Applications/Accessories/terminal and then entering ```
uname -r
```at the command prompt to find your kernel version.  
b.Then I would open Synaptic Package Manager by clicking on System/Administration/Synaptic Package Manager.
Then search for those two files and install them with Synaptic. 

> 1. Download the Linux Drivers from the Website.

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU)

They are the RTL8192CU for Linux/Unix.

The file I downloaded was called RTL8192CU_linux_v3.0.2164.20110715.zip
> 2. Extract the file.
   a. Right click on the file and click on extract here.
> 3. Copy the file to a directory of your choice.
   a. Open a terminal by clicking on applications/accessories/terminal
   b. Enter command ```
sudo nautilus
```at the command prompt. Enter your password if required.
      
   c. Move to the desired destination directory with the arrow buttons in nautilus.
   d. Copy the file from it's present location to the desired location in nautilus by right clicking on the file and clicking copy. Then paste it into the desired location by right clicking in the open nautilus window and clicking paste.
> 4. Change permissions on the install.sh script file
   a. Open the RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715 folder in nautilus.
   b. Right click on the install.sh file.
   c. Click on properties.
   d. Click on the permissions tab.
   e. Click in the "Allow executing file as program" box.  Make sure it has a check mark in it.
   d. Close the nautilus window by clicking the "x".
   e. Close the terminal by clicking on the "x".
> 5. Execute the installer script.
   a. Open a new terminal by clicking on Applications/Accessories/terminal
   b. cd or change directory to where you moved the file to. eg. ```
cd /opt/
```.
   c. Enter ```
sudo ./install.sh
```at the command prompt. Enter your password if required.
   d. Wait for the script to install your driver.
   e. Close the terminal window.
> 6. Your done! No duct tape required!

> 7. There is probably a better way to do this but I figured what the hey!

---

