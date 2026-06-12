---
title: "New to Linux"
date: 2010-06-02
forum: Multimedia Software
---

### Post by DriftingSilently86 on 2010-06-02
Hey Guys,
          I'm new to Linux so I don't know that much about it. I recently installed Ubuntu 10.04 LTS on my HP Pavilion dv4. It has an AMD x86 Architecture and did have Win7 on it. But I'm getting fed up with Windows. I am currently in the National Guard and am deployed in Iraq. I have to deal with computers all day, everyday. I just hate Windows now. But anyways, I switched to Ubuntu and I found that I needed to install alot of plugins to get the machine working how I want it. I need to install the Windows Media Audio & Encoder plugins to play music. Also I need the dvd encoder and mp3 codec. The problem is I can't find them. Ive looked everywhere and all of them only go up to Ubuntu 6 or 7 version. Where can I find a list of Ubuntu 10 codecs that will work with my amdx86 computer? Thanks in advance.

---

### Post by xc3RnbFO8P on 2010-06-02
> **DriftingSilently86 said:**
> Hey Guys,
          I'm new to Linux so I don't know that much about it. I recently installed Ubuntu 10.04 LTS on my HP Pavilion dv4. It has an AMD x86 Architecture and did have Win7 on it. But I'm getting fed up with Windows. I am currently in the National Guard and am deployed in Iraq. I have to deal with computers all day, everyday. I just hate Windows now. But anyways, I switched to Ubuntu and I found that I needed to install alot of plugins to get the machine working how I want it. I need to install the Windows Media Audio & Encoder plugins to play music. Also I need the dvd encoder and mp3 codec. The problem is I can't find them. Ive looked everywhere and all of them only go up to Ubuntu 6 or 7 version. Where can I find a list of Ubuntu 10 codecs that will work with my amdx86 computer? Thanks in advance.

(Lucid 32 bit) 
In Terminal one by one:
> sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
> sudo apt-get install libdvdcss2
> sudo apt-get install w32codecs
> 
sudo apt-get install libdvdread4
> sudo /usr/share/doc/libdvdread4/install-css.sh
You can check in Ubuntu Software Center for more Codec and Software (in View choose All Software) , just type **codec** in search window.

---

### Post by Rasa1111 on 2010-06-02
or if you want it easier~

just install Ubuntu restricted extras~
That has always worked for everything I need. 

in Software center, {Applications menu, at the bottom is software center}
type "restricted extras" into the search box at top right. 
Then install it. 

VLC might be something youll want also.
It plays *most* everything without additional codecs. 

 But get the Ubuntu restricted extras first~
see if that doesnt solve your issues. 

 If you dont want to use software center, and want to use the terminal,
Just open terminal and put 
> sudo apt-get ubuntu-restricted-extras
then your password, and it will install everything youll probably need.

[http://www.kartook.com/2010/05/ubuntu-how-to-install-ubuntu-restricted-extras-on-ubuntu-10-04lucid/](http://www.kartook.com/2010/05/ubuntu-how-to-install-ubuntu-restricted-extras-on-ubuntu-10-04lucid/)

ohh, welcome here,
and thank you. <3
Blessings

---

