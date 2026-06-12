---
title: "Mythbuntu 11.04 - repo upgrade problem"
date: 2012-06-25
forum: Mythbuntu
---

### Post by neutron68 on 2012-06-25
I've still got 11.04 running.  I'm trying to do an update inside the 0.24 repo, but I keep getting an error and it's stopping the full update.  It seems like adobe-flashplugin has some sort of name mismatch (like it was renamed to iceape-flashplugin??) and it can't be removed or re-installed.

What should I do?  
1.  Try and fix the update problem (and how do I fix) or 
2.  Plow forward and do an update to Mythbuntu 11.10, hoping that will fix the problem?

Here are some screen photos to show what I'm seeing.

Eric

[http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu%2011-04%20update/ResizeofDSCN4552.jpg](http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu%2011-04%20update/ResizeofDSCN4552.jpg)

[http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu%2011-04%20update/ResizeofDSCN4553.jpg](http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu%2011-04%20update/ResizeofDSCN4553.jpg)

[http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu%2011-04%20update/ResizeofDSCN4554.jpg](http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu%2011-04%20update/ResizeofDSCN4554.jpg)

[http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu%2011-04%20update/ResizeofDSCN4551.jpg](http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu%2011-04%20update/ResizeofDSCN4551.jpg)

[http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu%2011-04%20update/ResizeofDSCN4548.jpg](http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu%2011-04%20update/ResizeofDSCN4548.jpg)

[http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu%2011-04%20update/ResizeofDSCN4555.jpg](http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu%2011-04%20update/ResizeofDSCN4555.jpg)

---

### Post by Lester_Burnham on 2012-06-26
Hi,

Try going into synaptic package manager and search filters on the left I think.
Go to broken packages and try and remove from there. You will more than likely need to fix it before going any further.

Lester

---

### Post by neutron68 on 2012-06-26
> **Lester_Burnham said:**
> Hi,

Try going into synaptic package manager and search filters on the left I think.
Go to broken packages and try and remove from there. You will more than likely need to fix it before going any further.

Lester
That is the logical thing to try, and I did last weekend.  
I got a similar error message from the Synaptic Package Manager that I get when trying to upgrade with the Update Manager.

[http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu%2011-04%20update/ResizeofDSCN4554.jpg](http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu%2011-04%20update/ResizeofDSCN4554.jpg)

That's what I meant when I said I can't remove adobe-flashplugin or re-install it.

Am I going to have to find and edit the "pre-removal script" mentioned in error messages.
Any idea where those scripts are?

Eric

---

### Post by Lester_Burnham on 2012-06-26
Hi,

Try doing a search on Ubuntu force adobe-flash removal or install.
Lots of hits.

Lester

---

### Post by neutron68 on 2012-06-26
> **Lester_Burnham said:**
> Hi,

Try doing a search on Ubuntu force adobe-flash removal or install.
Lots of hits.

Lester
Good idea on the search terms.  I did't get ANY related hits when I searched the Ubuntu forums for "adobe-flashplugin".  

I did find a couple of links with procedures to try:
[http://ubuntuforums.org/showthread.php?t=1973994&highlight=force+adobe-flash+install](http://ubuntuforums.org/showthread.php?t=1973994&highlight=force+adobe-flash+install)
[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)
[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/) 

I figured that this flashplugin problem was probably a widespread, but it doesn't seem so?  
How come my system is the only one with this odd broken package problem?

Update:

I did this and it seemed to work:

```
cd /var/lib/dpkg/info/
sudo rm adobe-flashplugin.*
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
sudo apt-get install -f
sudo apt-get update
```

All seems happy again.

I still don't know why it went sour??

Eric

---

### Post by Lester_Burnham on 2012-06-26
Hi,

It's not just your system, I've had it a few times with different packages. You just need to fix the broken packages before moving on.

If you wait a little before upgrades, you'll find others have sorted the issues already, as you've done. :)

Lester

---

