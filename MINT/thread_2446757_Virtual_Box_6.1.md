---
title: "Virtual Box 6.1"
date: 2020-07-06
forum: MINT
---

### Post by Norrin Radd on 2020-07-06
I'm starting a separate thread because I think my issue might be different from [this one]("https://ubuntuforums.org/showthread.php?t=2444997").

I'm pretty much of a noob, sporadically tinkering with Linux Mint for a few weeks now.

My current goal is to install Windows 7 in VirtualBox, so I first need to get VB working.

I installed the VirtualBox that appears in the Software Manager.  It was 5.something.  I started following online instructions for setting it up for Windows 7, but it would not allow me to choose a 64-bit version.  I knew a newer version of VB was available and decided to try that, so I uninstalled the one from Software Manager.  (I went to the icon in the Cinnamon menu, right-clicked, and chose Uninstall.)

I went to Oracle and downloaded the .deb file for 6.1.10, located it on my system, right-clicked on it, and chose "Open with GDebi Package Installer."  That brought up the message, "Same version is available in software channel.  You are recommended to install it from there instead."  I assumed it was talking about Software Manager, and I knew it was not the same version, so I dismissed the warning and proceeded.

That did not solve the "64-bit" issue, so I looked around more online and found the suggestion to check my BIOS settings.  For some reason "Virtualization" was not enabled.  After I changed those settings and tried again, 64-bit OSes were available.  I completed the process of setting up memory, hard disk, etc., and was ready to begin actually installing Windows.  When I pressed the "Start" button in VB, I got an error message that the VirtualBox kernel modules do not match this version of VirtualBox; I could not proceed.

I uninstalled it via the Cinnamon menu, looked around a bit, and found the same version in the Package Manager.  I installed from there and did not get the message about "Same version is available in software channel," but ultimately ended up with the same error message.

I get the impression I need to do some sort of more thorough uninstall and reinstall, but don't know how.

Can anyone help?

---

### Post by SeijiSensei on 2020-07-06
If you don't mind mucking around at the command prompt, follow the instructions at [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions) to add the Oracle repository for VirtualBox and the necessary keys.  Then you can install 6.1 with
```

sudo apt update
sudo apt install virtualbox-6.1

```
It will be automatically updated the same way your other software is now.

If you're using 20.04, the line that begins with "deb" in the instructions linked above should read:
```
deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian focal contrib
```

You will need to use "sudo" to make the required changes to sources.list.  You might consider instead creating a separate file in the /etc/apt/sources.list.d/ directory instead like this:
```

echo 'deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian focal contrib' | sudo tee /etc/apt/sources.list.d/virtualbox.list

```
You will be prompted for your password.

Then proceed with the update/upgrade steps.

---

### Post by Norrin Radd on 2020-07-07
Ok... I understood barely anything at the virtualbox.org link.

Should I assume I'm too stupid to operate at that level, and just try sticking with the old 5.something version in Software Manager?

I'm still using Linux Mint 19.3

---

### Post by ajgreeny on 2020-07-07
I am pretty sure Mint 19.3 is based on Ubuntu 18.04 so you can use the instruction on that Vbox page linked by SeijiSensei above and follow the section for **Debian based operating systems**.

Run the two commands needed to add both the source to your system and the authorization needed ```
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -

``` 
Copy these two rather than type them as it's very easy to miss the final - in each command.
Now run ```
sudo apt update
sudo apt install virtualbox-6.1
```
It is also worth downloading the guest-additions package from the Vbox site; once it's downloaded double click it to install it in Virtualbox.
[https://download.virtualbox.org/virtualbox/6.1.10/Oracle_VM_VirtualBox_Extension_Pack-6.1.10.vbox-extpack](https://download.virtualbox.org/virtualbox/6.1.10/Oracle_VM_VirtualBox_Extension_Pack-6.1.10.vbox-extpack)

---

### Post by Norrin Radd on 2020-07-07
> **ajgreeny said:**
> I am pretty sure Mint 19.3 is based on Ubuntu 18.04 so you can use the instruction on that Vbox page linked by SeijiSensei above and follow the section for **Debian based operating systems**.

I don't understand the part about "Add the following line to your /etc/apt/sources.list."

I don't understand how to "download" the public keys.

Like I said, I understand almost nothing at that link.

---

### Post by SeijiSensei on 2020-07-07
We've tried to make this as simple as possible.  Let's try again.

First lets start with the basics.  Hold down Ctrl and Alt and press T to get a terminal.
Now, to download the keys, copy and paste the commands ajgreeny presented.

> **ajgreeny said:**
> Run the two commands needed to add both the source to your system and the authorization needed 
```
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -

``` 
Copy these two rather than type them as it's very easy to miss the final - in each command.

Next, you have to add the Oracle repository to your sources.  I gave you the exact command to do that.  However if Mint 19.3 is based on Ubuntu 18.04 ("Bionic Beaver"), you need to modify that command slightly.  So next, copy and paste this into the terminal:
```
echo 'deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian bionic contrib' | sudo tee /etc/apt/sources.list.d/virtualbox.list
```

Finally, run
```

sudo apt update
sudo apt install virtualbox-6.1

```

It might take a bit of work to get comfortable using the terminal, but it's worth it.

---

