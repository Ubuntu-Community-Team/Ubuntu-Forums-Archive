---
title: "Medibuntu Installation Trouble"
date: 2008-08-01
forum: Multimedia Software
---

### Post by Etheredge on 2008-08-01
Im trying to install medibuntu and was following the steps to the "Comprehensive Multimedia & Video How-to" and i am unable to actually install medibuntu if you will.


> etheredge@etheredge-laptop:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
OK
E: The method driver /usr/lib/apt/methods/https could not be found.
E: The method driver /usr/lib/apt/methods/https could not be found.

Also when i tried to add the source for the second one this is what i got on the terminal 

> etheredge@etheredge-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
--09:21:23--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[====================================>] 226           --.--K/s             

09:21:24 (19.53 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

etheredge@etheredge-laptop:~$ 
etheredge@etheredge-laptop:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
OK
E: The method driver /usr/lib/apt/methods/https could not be found.
E: The method driver /usr/lib/apt/methods/https could not be found.
etheredge@etheredge-laptop:~$ 



> IMPORTANT: If you haven't already, you need to enable the Medibuntu repository. The first command below is aimed at Ubuntu Family 8.04 Hardy Heron users and the manual instructions are also, so if you are using a different version of Ubuntu, you will have to slightly edit the command and sources. If you do have to edit the command, you can do so within the terminal by navigating to the word "hardy" with the keyboard arrow keys, change it to whatever version you are running and then move the cursor back to the end of the line before executing the command.

Quick Method: Open the terminal (Applications > Accessories > Terminal or KMenu > System > Terminal Program (Konsole) in Kubuntu and Applications > System > Terminal in Xubuntu) and paste these wget commands into it:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Manual Method: If the above method didn't work and you received an error, you will have to add the repository manually, which is actually quite easy. First of all, you need to open the sources file with your default or favourite text editor (replace "gedit" with "kwrite" in Kubuntu and "mousepad" in Xubuntu:

gksudo gedit /etc/apt/sources.list

Add the following two lines to the bottom of the list, remembering to change the Ubuntu version accordingly. After you have added the two lines, close and save the sources file:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

Finally, install the Medibuntu key by copying and pasting the following command into the terminal:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

