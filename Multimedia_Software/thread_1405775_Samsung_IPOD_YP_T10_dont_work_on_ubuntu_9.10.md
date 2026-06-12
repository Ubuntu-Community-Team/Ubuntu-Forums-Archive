---
title: "Samsung IPOD YP T10 dont work on ubuntu 9.10"
date: 2010-02-13
forum: Multimedia Software
---

### Post by emma00 on 2010-02-13
My samsung ipod yp-T10 works fine on windows but it does not on ubuntu.I have not installed any software to run it on ubuntu except there is Rythmbox and it does nothing when i scan the removable media.Whenever i try to open the music folder of my ipod it gives this error:



The folder contents could not be displayed.

Sorry, could not display all the contents of "Music": Failed to get file list: -8: Fixed limit exceeded.

Any ideas what should i do to synchronize it with Ubuntu.:???:

---

### Post by hughes532001 on 2010-02-18
Hi 

I have got mine to work in 9.10 using **amaroc** from Synaptic Package Manager but you may also need

mtpfs
mtp-tools
python-pypmtp

I installed those to try to get Rhythmbox to work with my Samsung T10 but I never had any luck it just crashed everytime I tried.  I have not deleted them so I don't know if they are really necessary.

Amaroc took me a bit of time to get used to, but it was worth the effort.

Regards

Trevor

---

### Post by emma00 on 2010-02-19
> **hughes532001 said:**
> Hi 

I have got mine to work in 9.10 using **amaroc** from Synaptic Package Manager but you may also need

mtpfs
mtp-tools
python-pypmtp

I installed those to try to get Rhythmbox to work with my Samsung T10 but I never had any luck it just crashed everytime I tried.  I have not deleted them so I don't know if they are really necessary.

Amaroc took me a bit of time to get used to, but it was worth the effort.

Regards

Trevor

Thanks but i could not find it in **Synaptic Package Manager** and also checked in **Ubuntu Software Center.**

Any Suggestions???

---

### Post by Julita on 2010-02-19
The player is **amaroK** it is there!

---

### Post by emma00 on 2010-02-19
> **Julita said:**
> The player is **amaroK** it is there!


thanks Julita

---

### Post by emma00 on 2010-02-19
Can you me tell me how you configured ipod with it?

Am not getting it!!!

---

### Post by Julita on 2010-02-19
[http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/)
this should help!

---

### Post by emma00 on 2010-02-24
it did'nt work:confused:

---

### Post by Julita on 2010-02-24
OK, apart from Amarok, there are also Banshee and gtkpod that work well with ipod. You might try this: [http://www.simplehelp.net/2007/07/07/how-to-use-gtkpod-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/07/how-to-use-gtkpod-to-manage-your-ipod-in-ubuntu/)

---

### Post by emma00 on 2010-02-28
> **Julita said:**
> OK, apart from Amarok, there are also Banshee and gtkpod that work well with ipod. You might try this: [http://www.simplehelp.net/2007/07/07/how-to-use-gtkpod-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/07/how-to-use-gtkpod-to-manage-your-ipod-in-ubuntu/)

I used gtkpod but it does not load my ipod and also followed the steps in the link you provided many users are having the same problem on that page anywaz thank you so much for your time and help.

---

### Post by Julita on 2010-02-28
Then I guess there is only one way left - install wine (it's the application that allows to run .exe in Linux)
sudo apt-get install wine
Then download iTunes - older 7.X version (the new ones don't work) from here: [http://www.oldapps.com/itunes.php?old_itunes=33?download](http://www.oldapps.com/itunes.php?old_itunes=33?download) When you click on .exe, it will launch automatically using wine.

---

### Post by emma00 on 2010-03-01
> **Julita said:**
> Then I guess there is only one way left - install wine (it's the application that allows to run .exe in Linux)
sudo apt-get install wine
Then download iTunes - older 7.X version (the new ones don't work) from here: [http://www.oldapps.com/itunes.php?old_itunes=33?download](http://www.oldapps.com/itunes.php?old_itunes=33?download) When you click on .exe, it will launch automatically using wine.


Ok i will give it a try and thanks so much :KS

---

### Post by eddier on 2010-03-01
Dont forget the poster is talking about SAMSUNG YP10 not IPOD by APPLE.

eddie

---

### Post by Julita on 2010-03-01
> **eddier said:**
> Dont forget the poster is talking about SAMSUNG YP10 not IPOD by APPLE.

I know, but sometimes which is supposed to work doesn't, and vice versa. Experiments is the best approach. :p

---

### Post by jzaragoza on 2010-03-01
> **Julita said:**
> I know, but sometimes which is supposed to work doesn't, and vice versa. Experiments is the best approach. :p
Is it true that the problem with IPods will be solved by 10.04 Lucid Lynx?

---

### Post by emma00 on 2010-03-01
> **Julita said:**
> Then I guess there is only one way left - install wine (it's the application that allows to run .exe in Linux)
sudo apt-get install wine
Then download iTunes - older 7.X version (the new ones don't work) from here: [http://www.oldapps.com/itunes.php?old_itunes=33?download](http://www.oldapps.com/itunes.php?old_itunes=33?download) When you click on .exe, it will launch automatically using wine.


No it didn't work.

---

### Post by Julita on 2010-03-01
Then please check here: [http://ubuntuforums.org/showthread.php?t=651894](http://ubuntuforums.org/showthread.php?t=651894) the user provides solution for your player; you need to install specific aplications...

---

### Post by Julita on 2010-03-01
> **jzaragoza said:**
> Is it true that the problem with IPods will be solved by 10.04 Lucid Lynx?

Who knows? You can now download the existing Lucid version and see if everything works. I think that the issue here is the manufacturer - this specific model sometimes doesn't work in Windows, with all the software installed...

---

### Post by emma00 on 2010-03-02
> **Julita said:**
> Then please check here: [http://ubuntuforums.org/showthread.php?t=651894](http://ubuntuforums.org/showthread.php?t=651894) the user provides solution for your player; you need to install specific aplications...


ok i will give it a try by the way r  u a girl????

If u r than happy to see u:D:D:D

---

