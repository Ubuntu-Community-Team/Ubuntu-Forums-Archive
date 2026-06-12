---
title: "Ubuntu 11.04 - poor stability after updates"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by lan3y on 2011-04-08
I've been running 11.04 for a while now, after performing updates yesterday the system has become very unstable.

- unity doesn't work anymore, no panels display when logging in to unity environment.
- kde 4.6.2 : black background only opens an terminal window, no other objects visable.
- an error about the ICEsecurity file could not be updated when logging on through KDM.

after logging on, ubuntu-one crashes most of the time (8 or 9 error windows piled on top of each other). 

I'm not sure where to start with these problems, can i have some advice?

I'm currently running an acer aspire one, 1gb ram, 160gb hdd, intel graphics, intel atom 1.6ghz.

Thanks
lan3y ):P

---

### Post by imigueldiaz on 2011-04-08
> **lan3y said:**
> 

- unity doesn't work anymore, no panels display when logging in to unity environment.
- kde 4.6.2 : black background only opens an terminal window, no other objects visable.
- an error about the ICEsecurity file could not be updated when logging on through KDM.


Thanks
lan3y ):P

You made a safe-ugrade? could be that the upgrade deleted or broke your gnome-session or kde related package. That happened me past Tuesday, and I had to reinstall gnome-session and ubuntu-desktop packages.

Hope It helps...

Best
Iñaki

---

### Post by lan3y on 2011-04-08
thanks for the reply,

i assume it was a safe upgrade, i let it run unattended due to the amount of time it takes.

which log files could i check for errors?

thanks
lan3y):P

---

### Post by 23dornot23d on 2011-04-08
> 
kde 4.6.2 : black background only opens an terminal window, no other objects visable.


I had that too a minute ago ..... in the terminal type 

sudo apt-get update
sudo apt-get install aptitude
sudo aptitude install kde-full

solved it for me .......... kde is good .... everything is working well ..... so far ....

can't say the same for UNITY with applications though ..... Freecad crashes and Gimp has no menus .....

---

### Post by lan3y on 2011-04-08
> **23dornot23d said:**
> I had that too a minute ago ..... in the terminal type 

sudo apt-get update
sudo apt-get install aptitude
sudo aptitude install kde-full

solved it for me .......... kde is good .... everything is working well ..... so far ....

can't say the same for UNITY with applications though ..... Freecad crashes and Gimp has no menus .....

ok thanks will try it when i get home, on the college grid at the moment.

I like the idea of unity, but its still very unstable, but a big improvement as the updates have rolled on.

lan3y

---

### Post by 23dornot23d on 2011-04-08
Also I found unity will only work from GDM .......

we seem to have a slight problem here .....

[COLOR=Red]**KDM**[/COLOR] will run both KDE and CLASSIC ....... ( UNITY has no menus or anything useable )

[COLOR=Red]**GDM**[/COLOR] - no more any options / choices for other systems that I can see ,,,


So if you want unity back ...... install another desktop manager and choose GDM ...... but be aware that it only seems to run UNITY ...... as the menu option button on the login screen is no longer there to change between systems ....... unless its hidden .......

Best of Luck ....... someone else may be able to shed more light on this .....

At the moment I prefer KDE and Classic so I use the KDM start  ...... would be nice to be able to boot into either ...... maybe someone has a script for this to  ask which desktop manager to load at boot into NAtty.

---

### Post by benjamimgois on 2011-04-08
> **lan3y said:**
> I've been running 11.04 for a while now, after performing updates yesterday the system has become very unstable.

- unity doesn't work anymore, no panels display when logging in to unity environment.
- kde 4.6.2 : black background only opens an terminal window, no other objects visable.
- an error about the ICEsecurity file could not be updated when logging on through KDM.

after logging on, ubuntu-one crashes most of the time (8 or 9 error windows piled on top of each other). 

I'm not sure where to start with these problems, can i have some advice?

I'm currently running an acer aspire one, 1gb ram, 160gb hdd, intel graphics, intel atom 1.6ghz.

Thanks
lan3y ):P

Same here. Sometimes i got to boot in classical mode but than nautilus doesn´t work and firefox takes looots of CPU! I´ve always update my installation on the beta stage and until maverick it worked just fine, but the beta stage of natty is not usable so far.

---

### Post by lan3y on 2011-04-08
thanks for the replies, 

I have now managed to get kde working, 

how do i change the display manager back to gdm?

thanks
lan3y):P

---

### Post by 23dornot23d on 2011-04-08
sudo apt-get remove kdm

choose gdm when it asks you which desktop manager you want ..... to run on next boot up.



> 
or the full way of doing this properly with gdm

sudo apt-get remove gdm
(but watch out - it may want to remove a  load of other stuff doing it this way)
sudo apt-get install gdm


There may be other ways ..... but these are the ones I use ,,,,,,

if you need kdm back at all

(sudo apt-get install kdm)
and then choose kdm .... when it asks you which desktop manager to use

---

### Post by thaDM on 2011-04-10
I agree with it recently becoming more unstable: ubuntu keeps randomly logging me out. But because I don't know what's causing it, I can't reproduce it for a bug report. Anybody else been logged out for no reason recently?

---

