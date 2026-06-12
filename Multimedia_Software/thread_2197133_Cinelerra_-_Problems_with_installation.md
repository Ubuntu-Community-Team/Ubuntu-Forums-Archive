---
title: "Cinelerra - Problems with installation"
date: 2014-01-02
forum: Multimedia Software
---

### Post by gianfranco2 on 2014-01-02
After adding Cinelerra to my list of repositories (sudo apt-add-repository ppa:cinelerra-ppa/ppa), and running *sudo apt-get update* and *sudo apt-get install cinelerra-cv*, I got the following error messages:
```
*cannot open locale definition file `de_DE': No such file or directory*
*dpkg: error processing cinelerra-cv (--configure):*
* subprocess installed post-installation script returned error exit status 4*
```
However, Cinelerra appears to have been installed and can be launched without significant problems; but now Cinelerra displays the following errors:
```
voidMWindow::init_shm():WARNING: /proc/sys/kernel/shmmax is 0x2000000, which is too low
Before running Cinelerra do the following as root:
echo "0x7fffffff" >/proc/sys/kernel/shmmax
```
I wonder, do the above error messages constitute a problem and should they be treated with concern? I understand that this is probably some minor issue, given the fact that the program runs, but still, is it likely to cause any problems in the future?

---

### Post by fghj8812 on 2014-01-03
> **gianfranco2 said:**
> 
For Cinelerra - no problem. But you will have problems with the installation and removal of other programs.
Simply make a now:
```
sudo rm /var/lib/dpkg/info/cinelerra-cv.postinst
```
```
sudo dpkg --configure -a
```

If you look at the script cinelerra-cv.postinst, you'll see it: 
> ...**# this add iso-8859-15 to all language suppoted by cinelerra**
**for i in de_DE es_ES fr_FR it_IT pt_BR sl_SI eu_ES eu_FR **
do 
if ! localedef --list-archive | grep $i | grep iso885915
then localedef -c -i $i -f ISO-8859-15 $i.ISO-8859-15
.....
This script wants to add locale de_DE.ISO-8859-15, but does not find it in your system.

This is a frequent question. I already answered this question here [http://forum.ubuntu.ru/index.php?topic=232568.new;topicseen#new](http://forum.ubuntu.ru/index.php?topic=232568.new;topicseen#new) and make screenshots. But there it is written in :-) Russian.
---------------------

[QUOTE]
[http://forums.gentoo.org/viewtopic-t-792891-start-0.html](http://forums.gentoo.org/viewtopic-t-792891-start-0.html)
[I]shmmax is just the maximum  sized memory segment a process can request,  an increase shouldn't really  be a security issue, and the increase  they're asking for is only 4  times the default, which isn't that much. 
 
You can just add "kernel.shmmax 134217728" to /etc/sysctl.conf to have it set to 0x8000000 upon each boot. 
Alternatively you could just run the echo command as suggested, and then   run `echo 33554432 > /proc/sys/kernel/shmmax` to reset it to the   default when finished with cinerella, if you're really concerned about   it.[/I]

> [B][http://www.g-raffa.eu/Cinelerra/HOWTO/installation.html](http://www.g-raffa.eu/Cinelerra/HOWTO/installation.html)
How to approach the Cinelerra error message you get at start up[/B]

  When you start Cinelerra you get an error message saying:

     The following errors occurred:
void MWindow::init_shm0: WARNING:/proc/sys/kernel/shmmax is 0x2000000, which is too low.
Before running Cinelerra do the following as root:
echo "0x7ffffff">/proc/sys/kernel/shmmax 

 Actually this message is not an error, but rather a reminder.
shmmax is a configurable kernel parameter that defines the system-wide  maximum allowable shared memory. Shared Memory (shm) is an efficeint  means of passing data between programs. One program will create a memory  portion which other processes can access. This error message asks you to increase the shared memory allocated by  default on the Linux kernel.

 What to do?

 Option 1:
Ignore this message. You won’t get in any trouble because of this.

 Option 2:
Do what you are told. That is open a terminal and type:

   sudo echo "0x7ffffff">/proc/sys/kernel/shmmax 

 This command will increase the shared memory during your work session.

 Option 3:
Open a terminal and type:

   sudo sysctl -w kernel.shmmax=0x7fffffff 

 This way you have increased the shared memory permanently.

   [TABLE]
[TR]
[TD="class: icon"] [IMG]http://www.g-raffa.eu/Cinelerra/HOWTO/images/icons/note.png[/IMG][/TD]
[TD="class: content"] You can obtain the same effect by manually editing the configuration file for setting system variables.
Open a terminal and type:

   sudo gedit /etc/sysctl.conf 

 At the bottom of the file, add those lines:

 # Make Cinelerra happy

 kernel.shmmax=0x7fffffff

 Save and close.
This is another way to increase the shared memory permanently.[/TD]
[/TR]
[/TABLE]


---

### Post by gianfranco2 on 2014-02-01
Thank you for replying to my question! I am reinstalling the system now (upgrading to Xubuntu 13.10) but this information, I think, will definitely prove useful in the future when reinstalling the application.

---

