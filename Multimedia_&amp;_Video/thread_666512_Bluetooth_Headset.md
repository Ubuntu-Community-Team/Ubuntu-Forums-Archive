---
title: "Bluetooth Headset"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by gutsy_psu on 2008-01-13
Hi all, 
I'm trying to configure my bluetooth headset to run in gutsy particularly with skype.  
The attached screenshots shows the gbtsco application i'm using which clearly recognizes my headset.  But when i click use as active headset it just hangs.  (the fact it recognizes it seems to prove my bluetooth adapter and headset itself are compatiable).  Anyway it doesn't seem to make it active, in my system volume control, I see a new listing for BT headset (alsa mixer), which also shows up in skype, but i set both to the BT and still sound comes through regular laptop speakers.  Any suggestions on what I'm doing wrong?  Much thanks

---

### Post by gutsy_psu on 2008-01-15
anyone?

---

### Post by gutsy_psu on 2008-01-16
I thought this would be a commmon issue? but i gather not from the lack of response I'm getting?

---

### Post by gutsy_psu on 2008-01-16
ok, am I in the right section of the forum for this?  If not would someone please be kind enough to redirect me? :)

Secondly, I think it's the sound pref, the gbtsco tool, succesfully pairs, and lists the headset as active.    it says all i have to do is change it in sound preference, which it opens for you.  However the only Bt setting in sound pref is for default mixer  there are no BT options for movies/sound or sound events.  Please help!

---

### Post by pondochris on 2008-01-18
I'm having the same problem!!!
headset pairs and connects but in sound preferences I can't set it to work...the only options for input are for my soundcard but not bluetooth. I only get it in default mixer.  will not work in teamspeak or steam
please help us!!!:confused:

---

### Post by alexandersk on 2008-01-18
Have you tried to run btsco manually using the terminal instead of through the GUI?

Like this:

btsco MAC_ADDRESS_OF_BT_HEADSET

Then you might be able to see if it gives you any error messages.

You might want to try to use Bluez instead, which is the "modern" way of using a bluetooth headset.  All you have to do is edit .asoundrc in your home directory and add:

pcm.bluetooth {
   type bluetooth
   device 00:19:1F:24:B2:D1
}

You will then get a new device called bluetooth which you can use instead.

You can try it using mplayer:

mplayer -ao alsa:device=bluetooth SOUND_FILE.MP3

Hope you get it workin'

cheers,
Alex

---

### Post by alexandersk on 2008-01-18
Just wanted to tell you that if Bluez doesn't work for you with my brief explaination, you might to install a few packages and make some configuration changes... 

there's some information about how to do that at [http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)

---

### Post by pondochris on 2008-01-18
Thanks for your reply.  From your post I gather that by following your directions, and adding the device, my BT headet will show up when I go to system-preferences-sounds. I would then be able to set it as my default capture device and use it with pidgin, steam,etc.

I did try it with ekiga and it works because it gives me the option in the settings.  I am looking to use it with xfire-pidgin.

I will give it a try when I get home from work tonight.

Thanks!

---

### Post by da Wookiee on 2008-01-19
That Seems to have worked for getting sound to the bluetooth headset from banshee, but is there an easier way to just be able to change the output through the regular sound preferences?


I've got a bluetooth headset entry in the sound preferences but it seems to be just a placebo.

---

### Post by gutsy_psu on 2008-01-19
> **alexandersk said:**
> Have you tried to run btsco manually using the terminal instead of through the GUI?

Like this:

btsco MAC_ADDRESS_OF_BT_HEADSET

Then you might be able to see if it gives you any error messages.

You might want to try to use Bluez instead, which is the "modern" way of using a bluetooth headset.  All you have to do is edit .asoundrc in your home directory and add:

pcm.bluetooth {
   type bluetooth
   device 00:19:1F:24:B2:D1
}

You will then get a new device called bluetooth which you can use instead.

You can try it using mplayer:

mplayer -ao alsa:device=bluetooth SOUND_FILE.MP3

Hope you get it workin'

cheers,
Alex

I have hidden files  shown, but there is no .asoundrc in my home directory, and my searchs so far have been futile, any ideas where to find it?  thanks!

---

### Post by gutsy_psu on 2008-01-19
> **gutsy_psu said:**
> I have hidden files  shown, but there is no .asoundrc in my home directory, and my searchs so far have been futile, any ideas where to find it?  thanks!

also,
 # btsco 00:19:7F:2C:5C:C9
Error: hwdep next device (hw:0): Operation not permitted
Error: control open (hw:1): No such device
Error: Can't find device. Bail

---

### Post by alexandersk on 2008-01-20
Have you tried running btsco as root? Don't remember if it's necessary but it might very well be.

If you don't have a .asoundrc file you might not have alsa installed? I'm no alsa expert but make sure that you have also installed, if you do, you should have .asoundrc in your home directory.

---

### Post by alexandersk on 2008-01-20
If your app doesn't support selecting input/output device then I don't know of any other solution than setting the headset as default. Don't think it is possible to change through the regular sound preferences.


> **da Wookiee said:**
> That Seems to have worked for getting sound to the bluetooth headset from banshee, but is there an easier way to just be able to change the output through the regular sound preferences?


I've got a bluetooth headset entry in the sound preferences but it seems to be just a placebo.

---

### Post by gutsy_psu on 2008-01-20
> **alexandersk said:**
> Have you tried running btsco as root? Don't remember if it's necessary but it might very well be.

If you don't have a .asoundrc file you might not have alsa installed? I'm no alsa expert but make sure that you have also installed, if you do, you should have .asoundrc in your home directory.



First, I was in root for the errors I posted, secondly, I do have alsa installed (running alsamixer command successfully shows my sound card settings), but still not .asoundrc file.  Thanks for your help!

---

### Post by gutsy_psu on 2008-01-22
*bump*

---

### Post by gutsy_psu on 2008-01-24
anyone? why don't i have a .asoundrc file, or where could it be?

---

### Post by da Wookiee on 2008-01-25
Don't know why you wouldn't have one.  Mine was in my home directory, it was empty, but it was there.  If there's not one, use gedit or nano to make one and put in the suggested entry.  In the end this method worked, at least as far as Banshee is concerned.  I want a better way that works globally but I haven't found it yet.

---

### Post by divinebovine on 2008-02-14
As far as the .asoundrc file is concerned it is not necessary for alsa to run properly, it is only necessary if you need to tweak the default behavior or add more functionality.  So no need to worry about the missing file, just create it and add what alex suggested.

More details concerning this file can be found on Alsa's website here, [http://alsa.opensrc.org/.asoundrc]("http://alsa.opensrc.org/.asoundrc")

---

