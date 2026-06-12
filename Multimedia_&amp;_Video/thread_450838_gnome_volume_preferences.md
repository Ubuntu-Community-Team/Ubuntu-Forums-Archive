---
title: "gnome volume preferences"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by mwolfe on 2007-05-21
I've got two soundcards. One of them is a soundblaster live 5.1 and that is what i primarily use. The other is an integrated card (its refered to as HDA Intel). The main reason i switch is just because my sound card jack that is accessible to headphones is in the front of the computer is off the Intel card so when i want to listen to headphones i switch. 

So anyways, In edgy i could switch soundcards by going into system->preferences->sound and just switch the default device to whichever i wanted. Then i'd restart the application.  That doesnt work in feisty for whatever reason.. I found that by using asoundconf set-default-card Intel (or to Live) i could switch the card.

So i wrote a little script to switch between the cards real easy

```
#!/bin/bash
# Check if the script is being run as root exit if it is not.
def=`/usr/bin/asoundconf get defaults.ctl.card`
if [ $def = Live ]; then
        echo "setting Intel"
        sudo /usr/bin/asoundconf set-default-card Intel
else
        echo "setting Live"
        sudo /usr/bin/asoundconf set-default-card Live
fi
echo  now using card: `/usr/bin/asoundconf get defaults.ctl.card`
```

the script works good and will change between the intel and the live card. 

However now i'm getting nit picky i suppose, but i'd like to also make it so it switches the gnome volume properties to adjust the card taht i switched to.. Does anyone know if there is a command i can use to switch that?  Or if there is a text file somewhere i can switch the values of.. (not sure if i know how to do that yet in bash but i could probably figure it out)

I dont know why gnome can't integrate the two so that  when you switch the default soundcard it changes the volume control as well.

---

