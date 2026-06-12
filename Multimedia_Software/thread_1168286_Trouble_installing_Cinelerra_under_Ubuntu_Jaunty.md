---
title: "Trouble installing Cinelerra under Ubuntu Jaunty"
date: 2009-05-23
forum: Multimedia Software
---

### Post by einfeldt on 2009-05-23
[B]Hi, 

I am having trouble installing Cinelerra under Ubuntu Jaunty.  First, I tried to go to Synpatic Package Manager and install Cinelerra through Synaptic.  I clicked on reload to make sure that I had the most recent lists.  I then typed Cinelerra in the search box, which yielded no results.  

I then went to this page:[/B]

[http://ubuntuforums.org/showthread.php?t=492154](http://ubuntuforums.org/showthread.php?t=492154)

**Which advised you to follow the instructions here**

[http://cvs.cinelerra.org/getting_cinelerra.php#jaunty](http://cvs.cinelerra.org/getting_cinelerra.php#jaunty)

Which suggests that you click:

Just double click on the link [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) and install it with GDebi Package Installer. 

**I did click on that link, and received this terminal output:**

(Reading database ... 183339 files and directories currently installed.)
Preparing to replace akirad-keyring-and-mirrors 2009.01.30 (using /tmp/addakirad-1.deb) ...
 Removing any system startup links for /etc/init.d/akiradrelease ...
   /etc/rc0.d/K20akiradrelease
   /etc/rc1.d/K20akiradrelease
   /etc/rc2.d/S20akiradrelease
   /etc/rc3.d/S20akiradrelease
   /etc/rc4.d/S20akiradrelease
   /etc/rc5.d/S20akiradrelease
   /etc/rc6.d/K20akiradrelease
Unpacking replacement akirad-keyring-and-mirrors ...
Setting up akirad-keyring-and-mirrors (2009.01.30) ...
OK
update-rc.d: warning: /etc/init.d/akiradrelease missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/akiradrelease ...
   /etc/rc0.d/K20akiradrelease -> ../init.d/akiradrelease
   /etc/rc1.d/K20akiradrelease -> ../init.d/akiradrelease
   /etc/rc6.d/K20akiradrelease -> ../init.d/akiradrelease
   /etc/rc2.d/S20akiradrelease -> ../init.d/akiradrelease
   /etc/rc3.d/S20akiradrelease -> ../init.d/akiradrelease
   /etc/rc4.d/S20akiradrelease -> ../init.d/akiradrelease
   /etc/rc5.d/S20akiradrelease -> ../init.d/akiradrelease

**The dialog box for the window containing that terminal said that the package was successfully installed.**

Package 'addakirad-1.deb' was installed.  

[B]I then tried to launch cinelerra by going to Applications > Sound & Video but Cinelerra was not listed there.  

I then tried to launch Cinelerra from the command line with this command:[/B]

je@rb:~$ sudo cinelerra
[sudo] password for cje: 
sudo: cinelerra: command not found

**I made sure that I have the akirad jaunty main repository installed and I do:**

cje@rb:~$ sudo wget -q [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update
[sudo] password for cje: 
(Reading database ... 183339 files and directories currently installed.)
Preparing to replace akirad-keyring-and-mirrors 2009.01.30 (using addakirad.deb) ...
 Removing any system startup links for /etc/init.d/akiradrelease ...
   /etc/rc0.d/K20akiradrelease
   /etc/rc1.d/K20akiradrelease
   /etc/rc2.d/S20akiradrelease
   /etc/rc3.d/S20akiradrelease
   /etc/rc4.d/S20akiradrelease
   /etc/rc5.d/S20akiradrelease
   /etc/rc6.d/K20akiradrelease
Unpacking replacement akirad-keyring-and-mirrors ...
Setting up akirad-keyring-and-mirrors (2009.01.30) ...
OK
update-rc.d: warning: /etc/init.d/akiradrelease missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/akiradrelease ...
   /etc/rc0.d/K20akiradrelease -> ../init.d/akiradrelease
   /etc/rc1.d/K20akiradrelease -> ../init.d/akiradrelease
   /etc/rc6.d/K20akiradrelease -> ../init.d/akiradrelease
   /etc/rc2.d/S20akiradrelease -> ../init.d/akiradrelease
   /etc/rc3.d/S20akiradrelease -> ../init.d/akiradrelease
   /etc/rc4.d/S20akiradrelease -> ../init.d/akiradrelease
   /etc/rc5.d/S20akiradrelease -> ../init.d/akiradrelease

rm: remove write-protected regular file `addakirad.deb'? y
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                                                                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                             
Hit [http://repository.akirad.net](http://repository.akirad.net) akirad-jaunty Release.gpg                                 
Ign [http://repository.akirad.net](http://repository.akirad.net) akirad-jaunty/main Translation-en_US                      
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed Release.gpg         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/restricted Translation-en_US
Hit [http://repository.akirad.net](http://repository.akirad.net) akirad-jaunty Release               
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                                                         
Hit [http://repository.akirad.net](http://repository.akirad.net) akirad-jaunty/main Packages                                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/universe Packages
Reading package lists... Done
cje@rb:~$ cinelerra
bash: cinelerra: command not found
cje@rb:~$ 

[B]I am now just really flummoxed and would appreciate any help as to how to get Cinelerra installed on this system running Ubuntu Jaunty.  \

Thanks in advance[/B]

---

### Post by newseamus on 2009-05-24
same problem here with Intrepid...i amfrustrated

---

### Post by einfeldt on 2009-05-26
> **newseamus said:**
> same problem here with Intrepid...i amfrustrated

Hi,

Someone pointed out to me that what I did in the output that I posted above was to add the proper repository.  Now when I go into the Synaptic package manager and type "Synaptic" I see the option to add Cinelerra.  It's easy.  Just follow the instructions here, and then go back into Synaptic.  You should see Cinelerra there.

[http://cvs.cinelerra.org/getting_cinelerra.php#jaunty](http://cvs.cinelerra.org/getting_cinelerra.php#jaunty)

I hope this helps.

---

### Post by newseamus on 2009-05-26
I have the akirad repositories listed in my Synaptic....but no Cinelerra in the package list.
EDIT: as i wrote this post I thought to go look in the Akirad repository with synaptic, and alas I see all the Cinelerras listed! If I do a search in synaptic...shouldn't it look in ALL repositories for a match?

---

### Post by einfeldt on 2009-05-26
> **newseamus said:**
> I have the akirad repositories listed in my Synaptic....but no Cinelerra in the package list.
EDIT: as i wrote this post I thought to go look in the Akirad repository with synaptic, and alas I see all the Cinelerras listed! If I do a search in synaptic...shouldn't it look in ALL repositories for a match?

Did you reboot your computer?  Something similar happened to me.  I installed the repository as shown above.  Then I searched for Cinelerra.  Didn't see it.  Then, a day later, I searched again, and there was Cinelerra!  At that point, I just used Synaptic to download and install Cinelerra!  Kinda strange. For both you and me, Synaptic should have seen Cinelerra without rebooting! 

But the important thing is that I now have Cinelerra!

---

### Post by Polar Eyes on 2009-06-03
I had the same trouble with installing Cinelerra. It came down to finding a video on youtube basically saying that the quick search in synaptic doesn't ALWAYS reveal Cinelerra for installing. 

[Here]("http://www.youtube.com/watch?v=V1x0RjG7dz8") is the video I found.

Now onto the tut's!

---

### Post by Jesus.9.04 on 2009-08-12
Hello I recently tried to install cinelerra, and I followed all instructions from:

[http://cvs.cinelerra.org/getting_cinelerra.php#jaunty](http://cvs.cinelerra.org/getting_cinelerra.php#jaunty)

then went to sypnatc checked the repositories, reloaded sypnatic, then rebooted. 

Once rebooted I went back into sypnatic and searched for cinelerra and it was there, but, when I click on "check for installation" and I marked additional required changes, but when I hit apply to install this came up:

cinelerra:
 Depends: liblame0 (>=3.97) but it is not installable
 Depends: libmjpegtools0c2a (>=1:1.8.0) but it is not installable
 Depends: libopenexr2ldbl (>=1.2.2) but it is not installable
 Depends: libquicktimehv but it is not going to be installed

Then I went to Terminal and used:

~$ sudo aptitude install cinelerra
[sudo] password for jesus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages are BROKEN:
  cinelerra libquicktimehv 
The following NEW packages will be installed:
  libguicast{a} libmpeg3hv{a} 
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.7MB of archives. After unpacking 32.8MB will be used.
The following packages have unmet dependencies:
  cinelerra: Depends: liblame0 (>= 3.97) which is a virtual package.
             Depends: libmjpegtools0c2a (>= 1:1.8.0) which is a virtual package.
             Depends: libopenexr2ldbl (>= 1.2.2) which is a virtual package.
  libquicktimehv: Depends: liblame0 (>= 3.97) which is a virtual package.
                  Depends: libx264-57 (>= 1:0.svn20071224) which is a virtual package.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
cinelerra [Not Installed]
libquicktimehv [Not Installed]

Score is -9872

Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done



Then I went to applications>sound&video>

and cinelerra was STILL not there!?

Any help would be great. Thanks

[Edit] I am running Ubuntu 9.04 Jaunty Jackalope

---

### Post by mwpruett on 2009-09-25
The fix I got was to click origin in synaptic's package manager, and then click repository.akirad.net/main on the left, then all cinelerra packages were visible.

---

