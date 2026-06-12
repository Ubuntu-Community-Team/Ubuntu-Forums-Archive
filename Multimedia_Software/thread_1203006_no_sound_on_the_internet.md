---
title: "no sound on the internet"
date: 2009-07-02
forum: Multimedia Software
---

### Post by shaloken on 2009-07-02
Hi,
   sometimes, when I go to the internet and try to play a video on youtube (or any other websites) I have no sound. So I tried to play something with totem and it works. So the problem is just on the internet...
When I reboot my laptop, the sounds come back.

Thanks

---

### Post by shaloken on 2009-07-03
can someone help me?

It will be appreciated

Thanks

---

### Post by Th3_uN1Qu3 on 2009-07-03
Youtube is a flash site. Most media sites on the net are flash lately... That means your Flash Player isn't working properly. If you are using the open-source one try installing Adobe's player. It can be installed from Synaptic if i remember right.

---

### Post by shaloken on 2009-07-04
It was already installed. I re-install it and I restart my laptop but there is no change.

---

### Post by shaloken on 2009-07-05
I saw yesteray that I can hear sound on megavideo.
I don't know if they are using flash player but it seems it's different from  the others web sites.
If someone have any trick or have already pass trough this...

---

### Post by Kurou-san on 2009-07-05
Then try purging it from you system and trying it again or using the other like this:
```

#I'm not sure which one you used so I include both.
sudo aptitude update
sudo aptitude purge flashplugin-nonfree adobe-flashplugin

#try uncommenting one of these
#sudo aptitude install adobe-flashplugin 
#or
#sudo aptitude install flashplugin-nonfree

```

---

### Post by shaloken on 2009-07-05
when I do this line:
> sudo aptitude install flashplugin-nonfree

In the middle of all the tect there is that paragraph
> Downloading...
--20:48:15--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Résolution de fpdownload.macromedia.com... 96.6.66.70
Connexion vers fpdownload.macromedia.com|96.6.66.70|:80... connecté.
requête HTTP transmise, en attente de la réponse... 404 Not Found
20:48:15 ERREUR 404: Not Found.

download failed
The Flash plugin is NOT installed.



---

### Post by p0cky84 on 2009-07-05
```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```
# Restart Firefox

---

### Post by shaloken on 2009-07-05
Now it says that it's already installed
> flashplugin-nonfree est déjà la plus récente version disponible.
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.


Do you want me to purge it again?

---

### Post by gasto on 2009-07-06
Same problem for me, I am using the OSS sound device, because my Lambda Lexicon USB audio interface can only work that way.

Any help is really appreciated.

---

### Post by gasto on 2009-07-06
Tried installing

Flashplugin-nonfree-extrasound:

Adobe Flash Player platform support library for Esound and OSS

This is an open Source extension library for the Adobe Flash Player
that enables support for otherwise unsupported sound systems.  It
provides the libflashsupport.so plugin.  The sound system to use is
automatically detected:

 * It first tries to detect Esound,
 * Next, it checks for OSS.

If all of the above failed, it falls back to the ALSA driver that's
built directly into FlashPlayer 9.

For PulseAudio support, see flashplugin-nonfree-pulse.



But no luck even after restarting Firefox 3.0.11

---

### Post by gasto on 2009-07-06
I tried first this:

[http://newtoubuntu.wordpress.com/2009/04/25/ubuntu-904-no-sound-with-flash-videos/](http://newtoubuntu.wordpress.com/2009/04/25/ubuntu-904-no-sound-with-flash-videos/)

Then this:

[http://mikewilliamson.wordpress.com/2008/05/06/flash-sound-in-ubuntu-hardy-heron/](http://mikewilliamson.wordpress.com/2008/05/06/flash-sound-in-ubuntu-hardy-heron/)

But had no luck. Note that the latter link says:

sudo apt-get install libflashsupport

while it should be

sudo apt-get install flashplugin-nonfree-extrasound

And still sound on flash video does not work.

---

### Post by Kurou-san on 2009-07-06
> **shaloken said:**
> Now it says that it's already installed


Do you want me to purge it again?

Yeah, try purging it again. If all else fails, just download [this](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb)) and run it.

---

### Post by Ra-Hoor-Khuit on 2009-07-06
Install the Adobe flash plugin from Post #13 above.  [I]

Once it's installed, and not before[/I], open Synaptic Package Manager.

Search on **swfdec**.  Mark any  hits for removal and then "Apply" the changes.

Search on **gnash**.  Mark any hits for removal and then "Apply" the changes.

You should be good to go now.

---

### Post by gasto on 2009-07-07
I don't even have gnash nor swfdec-mozilla nor swfdec-gnome installed.

---

