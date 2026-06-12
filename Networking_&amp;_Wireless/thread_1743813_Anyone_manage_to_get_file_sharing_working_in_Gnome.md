---
title: "Anyone manage to get file sharing working in Gnome 3?"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by akand074 on 2011-04-29
Hey guys,

I've been getting rather frustrated trying to share a few folders with Windows PCs. Usually I just right click and choose "Sharing Options" from nautilus and choose to share it. This isn't there in gnome 3 via gnome3 ppa for Ubuntu. I've tried installing and adding the folders I wanted using samba configuration tool and gadmin-samba tools. I've also installed just about anything that could potentially have anything to do with file sharing from synaptic including: 

samba, nautilus-share, smbclient, windbind 

and whole lot of other stuff in hope that I had just been missing stuff. I also booted my laptop which is running 11.04 with Unity and I right clicked and selected "Sharing Options" like the usual way and shared a folder and then installed gadmin-samba and the samba configuration tools and the folder I shared wasn't included there. Meaning it isn't using the same thing? Also the only thing installed when shareing a folder is samba and some libpam-something. Two files! Then shares perfectly! Why is it so difficult to set up a simple share with Gnome 3? No matter what I do I boot into Windows on my laptop and try to connect to my network share the same way I always have and it doesn't work. 

Has anyone gotten file sharing using Gnome 3 working? I don't know why a shell should prevent me from doing this?

---

### Post by jerenept on 2011-04-29
try system-config-samba . (sudo aptitude install system-config-samba )

I thinkthe DE is not important to SAMBA, it may be another problem.

---

### Post by akand074 on 2011-04-30
> **jerenept said:**
> try system-config-samba . (sudo aptitude install system-config-samba )

I thinkthe DE is not important to SAMBA, it may be another problem.

Yeah that was the samba configuration tool I already tried as well. It's pretty much a simplified version of gadmin-samba. I added the folders there and Windows still can't find me at all in the network. The odd thing was that I installed system-config-samba on my laptop running Unity where I right clicked and added a folder to share and that folder did not show up among the folders in system-config-samba, and that's the way that has always worked for me so they must be different. I'm unsure why adding them there doesn't work. But I suppose it's not just that it can't find the folders but the computer can't find my system in the network at all. I don't know why there isn't the sharing options right in nautilus. Perhaps when/if Ubuntu officially supports a gnome 3 system they'll fix that up. This system is pretty unstable.

---

### Post by grege on 2011-05-02
There is probably a simpler solution, but what I have is Xubuntu installed in parallel.

When you log in to Xubuntu Nautilus has the share options tab and works like it always did. When finished setting it up log out and back into Gnome3

I am still looking for the Gnome3 way.

---

### Post by grege on 2011-05-02
I just checked and that approach does not work any more. 

The Nautilus in Xfce is the same one and the shares are gone.

Edit:

I have purged the Gnome3 PPA and gone to a vanilla Xubuntu with Nautilus and Nautilus-Share installed and Samba seems to be working. I have had to make too many concessions to both Unity and Gnome3 for me to use them in the current versions. I am officially an Xfce user on desktop and notebook.

Try again in six months. Yes I know I can use Gnome Classic, but that will be gone as an option at the next update while Xubuntu will soldier on.

---

### Post by akand074 on 2011-05-03
I was considering doing something like that. But I didn't want to purge gnome 3 again and then set up shares and then install gnome 3. And you just said it doesn't work anymore, so now it feels like a hassle to do it just to find out it doesn't work.

---

### Post by grege on 2011-05-03
> **akand074 said:**
> I was considering doing something like that. But I didn't want to purge gnome 3 again and then set up shares and then install gnome 3. And you just said it doesn't work anymore, so now it feels like a hassle to do it just to find out it doesn't work.

It might be possible to install KDE and set them up from there, but it might just go round and back to nothing. I cannot see why Gnome3 and KDE would not happily co-exist. I just ran out of patience, it may have been just a matter of starting Samba services inside Gnome3 to pick up the shares set up by Xfce. The problem was once set there was no adding new ones once Gnome3 is installed. You can manually create shares by looking in /var/lib/sambashare/ and following an example. 

So if you are game add KDE, setup shares then ensure Samba is loading when using Gnome3. I may have given up too easily, but then I am really liking Xubuntu so I no longer care.

---

### Post by akand074 on 2011-05-03
> **grege said:**
> It might be possible to install KDE and set them up from there, but it might just go round and back to nothing. I cannot see why Gnome3 and KDE would not happily co-exist. I just ran out of patience, it may have been just a matter of starting Samba services inside Gnome3 to pick up the shares set up by Xfce. The problem was once set there was no adding new ones once Gnome3 is installed. You can manually create shares by looking in /var/lib/sambashare/ and following an example. 

So if you are game add KDE, setup shares then ensure Samba is loading when using Gnome3. I may have given up too easily, but then I am really liking Xubuntu so I no longer care.

I may try something like that. I just find it ridiculous that gnome 3 makes it so complicated to share files. I'm thinking maybe when/if it's officially supported by Canonical or if a gnome-shell distribution is made that it'll make it more like the other Ubuntu releases.

---

### Post by akand074 on 2011-05-06
I actually booted into Unity from my laptop and set up shares in the three folders I wanted to share on my desktop and then copy/pasted over the config files to my desktop. Now Windows actually recognizes the network but it tries to login to user-pc (laptop) and not user-desktop and fails even though I couldn't find any reference to which system created the config files at all. This leads me to believe that if I did it through Unity on my desktop it should work fine? But unlike before I've actually used Gnome 3 for quite a while now and set up some stuff. I'm worried purging the gnome 3 ppa won't bring me to a workable Unity, or going back to gnome 3 might not give me a workable gnome 3 (and if it does work it might wipe my gnome 3 settings, or even worse the nautilus-share settings from Unity that created my shares so I should likely back those up). So I don't really know if it's worth the hassle. I do really like Unity, though I still think Gnome 3 generally would be better for my desktop and I would miss the notification system if I dropped back to Unity. Its just frustrating how difficult it is to set up a simple file share here when normally in Ubuntu I just right click the file and click share from the sharing options. I have nautilus-share installed, why is that feature not being added in nautilus when the package is installed?

---

### Post by matthewbpt on 2011-05-06
Install webmin ([www.webmin.com](www.webmin.com)). I is a web based administration tool which includes a samba configuration module which works really well!

---

### Post by Retlol on 2011-05-06
ssh?

---

### Post by akand074 on 2011-05-06
> **Retlol said:**
> ssh?


hah I SSH from Linux to Linux... not a chance for Windows. That's a pain. Especially for the rest of my family.

> **matthewbpt said:**
> Install webmin ([www.webmin.com]("http://www.webmin.com")). I is a web based administration tool which includes a samba configuration module which works really well!

I'll check this out.

---

### Post by akand074 on 2011-05-07
No luck with webmin.. it's exactly the same thing as system-config-samba it's just in a web interface instead. Nautilus-share does something completely different (creates a config file per folder within var/lib/samba/usershares) and that's the only way that has ever worked for me from Ubuntu. I may just drop back to Unity. Gnome 3 freezes on me all the time too. Perhaps I'll just wait until 11.10.

---

### Post by scpxi on 2011-05-09
I managed to get shares working using system-config-samba and then I moved my drive mount points to my home folder that's the easiest workaround i got to enable shares in Gnome 3.

p.s. this is my first post so pardon my lack of mannerisms if ever....:)

---

### Post by akand074 on 2011-05-09
> **scpxi said:**
> I managed to get shares working using system-config-samba and then I moved my drive mount points to my home folder that's the easiest workaround i got to enable shares in Gnome 3.

p.s. this is my first post so pardon my lack of mannerisms if ever....:)

Hey thanks, I actually ended up dropping gnome 3 for Unity for now as it was far from stable thus far. I'll decide whether to move back to gnome 3 in 11.10 or not. This turned into a support thread instead of just an inquiry, I'll see if a mod can have it moved so that maybe others can benefit.

---

### Post by overdrank on 2011-05-09
Moved to Networking & Wireless. :)

---

### Post by grege on 2011-05-26
I am nothing if not pig headed.

Install Kubuntu and get it all configured and functional. Set up your normal simple Samba shares. There are a few packages to install in KDE for file sharing, but easy stuff.

Then add the Gnome3 PPA and then using Synaptic add the Gnome3 stuff one by one, ignoring the Gnome2 stuff for now.

Now you have KDE and Gnome3 installed in parallel. From the login window select Gnome Shell and you are running. You will find that the shares setup by KDE are still sharing and devices like media players can see and use them. If you look at the network entry in Nautilus you can select your own computer and see the shared folders. There is no other indication that the folders are shared. At any time you can fire up Dolphin and edit the shares.

I have now added a few other bits and pieces to Gnome3 and it runs quickly and, so far, it is stable. I had to remove the ATI fglrx drivers and revert to the xorg driver, but that is no issue for me.

The Ubuntu Gnome Respin is out. I am interested to see if this issue is resolved, but I somehow doubt it. But, of course, all you need to do is install Dolphin and the KDE sharing apps and run them under Gnome3, and use Dolphin insteed of Nautilus for network operations.

---

