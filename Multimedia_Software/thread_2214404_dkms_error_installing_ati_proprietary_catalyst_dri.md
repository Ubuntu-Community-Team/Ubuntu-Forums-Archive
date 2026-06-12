---
title: "dkms error installing ati proprietary catalyst driver 13.12 in Ubuntu Saucy 13.10"
date: 2014-04-01
forum: Multimedia Software
---

### Post by peter_nz on 2014-04-01
Installing Ati Proprietary Drivers version catalyst 13.12 in Ubuntu 13.10 and you get a DKMS error!!!

Don't worry here is a list of "what you need to do."

Update your Saucy Installation.
Install all the prerequisite files you will need. We will need to install Synaptic package manager and add a repository from raring ringtail,
so we can get ia32-libs package As Ubuntu maintainers prematurely have removed it from the saucy repos.
Download the Ati Drivers from official site
Patch the driver cause its bugged (don't worry its pretty easy).
Create, distro specific .deb files of your drivers.
Install the drivers (.deb files)
Update your xorg.conf file to use the new drivers.
Reboot to see your new graphics :)
Note Well: when entering code into terminal by copy and paste please be sure to do it ONE line at a time unless I specifically state that you should do more which does happen on two occasions where the code to enter may on some systems overlap onto a second
This part is HOW you do it. ie: the code to enter in terminal to get it done.

```
sudo apt-get update && sudo apt-get upgrade
``` 
```
sudo apt-get install synaptic
```
Launch synaptic and goto “settings > Repositories” click “other software > add” insert the following line in the pop up box

```
deb http://archive.ubuntu.com/ubuntu/ raring main restricted universe multiverse
```
Click "OK" button , you can now close synaptic. then update apt-get again.

```
sudo apt-get update
``` 

The following code line is long and may actually spans two lines , just copy and paste it in one go into terminal. 

```
sudo apt-get install ia32-libs lib32gcc1 libc6-i386 build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases
``` 

Now install linux-source not strictly necessary , but I say better safe than sorry. 

```
sudo apt-get install linux-source
``` 

Ok you are doing well now lets get the driver from ATI site using wget and create a new folder in your "home" directory to put it all in. 

```
cd ~/
``` 

```
mkdir catalyst13.12 && cd catalyst13.12
``` 

The following code line is long and may actually span onto a second line, just copy and paste it in one go in terminal. 
```
wget --referer='http://support.amd.com/en-us/download/desktop?os=Linux+x86' http://www2.ati.com/drivers/linux/amd-catalyst-13.12-linux-x86.x86_64.zip
``` 

```
unzip amd-catalyst-13.12-linux-x86.x86_64.zip
``` 

```
chmod +x amd-catalyst-13.12-linux-x86.x86_64.run
``` 

```
./amd-catalyst-13.12-linux-x86.x86_64.run --extract catalyst
``` 

```
cd catalyst
``` 

Now we will open the file that needs to be patched manually in gedit 

```
gedit common/lib/modules/fglrx/build_mod/kcl_acpi.c
``` 

Scroll down the file till you get to line 990 it should look like the following example.
 
        #if LINUX_VERSION_CODE >= KERNEL_VERSION(3,6,3)    
            if (!ACPI_SUCCESS(acpi_get_table_with_size(id, 0, &hdr, &tbl_size)))
        #else
            tbl_size = 0x7fffffff;
            if (!ACPI_SUCCESS(acpi_get_table(id, 0, &hdr)))
        ...
      
Now delete everything from line 990 (including line 990) to the end of the file and replace with this: 
```
#if LINUX_VERSION_CODE >= KERNEL_VERSION(3,6,3)    
            if (!ACPI_SUCCESS(acpi_get_table_with_size(id, 0, &hdr, &tbl_size)))
        #else
            tbl_size = 0x7fffffff;
            if (!ACPI_SUCCESS(acpi_get_table(id, 0, &hdr)))
        #endif
            {
                return KCL_ACPI_ERROR;
            }
        #if LINUX_VERSION_CODE >= KERNEL_VERSION(3,9,1)
            ((acpi_tbl_table_handler)handler)(hdr);
        #else
            ((acpi_table_handler)handler)(hdr);
        #endif
            return KCL_ACPI_OK;
        }
```
      


Now SAVE the file and close gedit. 
Wow we are almost finished, lets build the .debs now. 

```
sudo ./ati-installer.sh 13.251 --buildpkg Ubuntu/saucy
``` 

that should start creating the 3 .deb files When they are done, install them with the following command. 

```
sudo dpkg -i *.deb
``` 

Installed ? great now don't reboot just yet. You need one more command first, here it is. 

```
sudo aticonfig --initial
``` 

Now reboot your PC. 

```
sudo reboot now
``` 

Thats it well done, enjoy your better graphics performance.

---

