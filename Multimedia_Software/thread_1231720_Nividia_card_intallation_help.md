---
title: "Nividia card intallation help"
date: 2009-08-04
forum: Multimedia Software
---

### Post by cuzimjoesmith on 2009-08-04
Could not open the file /home/joesmith/Desktop/N…ux-x86-185.18.31-pkg1.run using the Unicode (UTF-8) character coding.


what does this mean. and how do i get it to open ?

---

### Post by genesisfactor on 2009-08-05
hey, why don't you try this in terminal

(shut down gdm first though)

cd Desktop

sudo ./N <<then hit tab>>

and it should work.  I is what i did.  There is a nice tutorial on some page...i will link you when i find it....

---

### Post by 3rdalbum on 2009-08-05
1. If you have installed the Nvidia driver previously through the Hardware Drivers program, or through Synaptic, you must remove it before manually installing the driver from Nvidia.com. Go into Synaptic and remove everything that begins with "nvidia-glx".

2. There are installation instructions on the Nvidia website; you don't double-click the installer, you have to shut down the X server first, and then run the program in the terminal. It's not a user-friendly process, but that's Nvidia's fault.

Install the "linux-headers" and "build-essential" packages from Synaptic - they are prerequisites.

Log out, press Control-Alt-F2 and log into the text terminal.

Type this:

```
sudo su
killall gdm
cd Desktop
./N (and then press Tab to autocomplete the full filename
```

The installer will do the rest. Answer Yes to everything. When it's finished and you're back at the command-line prompt, type:

```
gdm
```

And you should be running with the new driver.

---

### Post by cuzimjoesmith on 2009-08-05
3rdalbum-

ok just so i get everything right the first time i am going to ask you step by step if i am doing each step right.

so far before i read this i had alot(felt like alot) of stuff i installed to make it work and read many different ways but didnt seem to help.

but i went and uninstalled "nvidia-glx". but there were other none glx about nvidia that is installed do i just leave those alone?

and for the "linux-headers" there are several of them which one?

and for the "build-essentails" it says this -

("If you do not plan to build Debian packages, you don't need this
package.  Starting with dpkg (>= 1.14.18) this package is required
for building Debian packages") -- 

do i still install it ???

and i have read things baout the x-server and xfree86 of somthign like that does the code that you gave me is that to shut down the x-server ''
sudo su
killall gdm
cd Desktop
./N (and then press Tab to autocomplete the full filename
?

---

### Post by cuzimjoesmith on 2009-08-06
bump.

---

### Post by 3rdalbum on 2009-08-11
You can keep the nvidia packages that do not have "glx" in them. Or you can remove them. Up to you :-)

Sorry - it should have been "linux-headers-generic". If you don't already have the latest kernel, it will install it for you.

Install build-essential because it's the easiest way to get the compilers and basic development headers; the Nvidia driver installer needs a compiler in order to build an interface to your kernel.

Yep - "sudo su" runs the terminal as root (you need to be root to do these things). Killall gdm will stop the X server from running. Cd desktop will change the current directory to the desktop, where your Nvidia driver installer is (or rather, where you should put it for the time being!). And the "./N" and pressing Tab will complete the command to actually run the installer.

---

### Post by cuzimjoesmith on 2009-08-11
ok i have everything the first parts figured out but
 
: i type in sudo su and i type in my password and thn type in killall gdm and i get a black screen with lines that i dont understad ( i need to i can post waht i says).
 
when i tpe in cd desktop it says its not recognized.
 
and ./n doensnt do anything.

---

### Post by 3rdalbum on 2009-08-13
1. It's not "cd desktop", it's "cd Desktop".

2. You type ./N and then press Tab to autocomplete BEFORE you press Enter.

---

### Post by Deiu on 2009-08-13
I've posted a guide regarding the installation of nvidia drivers on my [blog page]("http://andrei.envisioningtech.net").

Here is a summary:

1. Press CTRL+ALT+F2 (or 3,4,5) to get to a console. Login using your username and password.

2. Stop gdm by typing: `sudo /etc/init.d/gdm stop`

3. Change dir to the one containing the Nvidia drivers (assuming they are on your desktop): `cd ~/Desktop`

4. Install drivers: `sudo sh Nvidia....pkg0.run` (start with the one containing 0)

5. Once you finish installing the drivers, start gdm again: `sudo /etc/init.d/gdm start`

6. ?????

7. Profit!

---

### Post by genesisfactor on 2009-08-25
> **Deiu said:**
> I've posted a guide regarding the installation of nvidia drivers on my [blog page]("http://andrei.envisioningtech.net").

Here is a summary:

1. Press CTRL+ALT+F2 (or 3,4,5) to get to a console. Login using your username and password.

2. Stop gdm by typing: `sudo /etc/init.d/gdm stop`

3. Change dir to the one containing the Nvidia drivers (assuming they are on your desktop): `cd ~/Desktop`

4. Install drivers: `sudo sh Nvidia....pkg0.run` (start with the one containing 0)

5. Once you finish installing the drivers, start gdm again: `sudo /etc/init.d/gdm start`

6. ?????

7. Profit!

That's how i did it after envyng..still no love.

---

### Post by raygj on 2009-08-28
> **genesisfactor said:**
> That's how i did it after envyng..still no love.
instead of 
"4. Install drivers: `sudo sh Nvidia....pkg0.run` (start with the one containing 0)"
use
"4. Install drivers: `sudo sh ./Nvidia....pkg0.run` (start with the one containing 0)"

---

