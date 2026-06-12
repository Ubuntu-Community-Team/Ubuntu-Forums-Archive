---
title: "New Myth Experiences so far - Scripts,Tuning etc.."
date: 2013-04-06
forum: Mythbuntu
---

### Post by rodneymckay7 on 2013-04-06
Hi

I have got MythTV both the Front end (v0.26.0-119-gc0419cd)
and the Backend installed on XUBUNTU 12.04.2 LTS 

I impressed with the amount of effort put into the development of mythtv.
Although disappointed with some things.

1-I had to go back to using my Sony Bravio TV Tuner because  my current tuner card does not seem to have a strong enough reception
Hauppauge Nova-T 500 DVB PCI tuner card  (I am in Australia)
I suspect this issue is one where I will have to bang my head against the wall - finding out how to improve the signal.

2-I have been dissapointed by the Movie Video Art importing as it only likes certain Filename-Folder structures
I am impressed that it works sometimes. I am wondering where the location of the scripts are to modify and improve this structure.
I would like to replace it with my own art, or even modify the themes..

3-When I rename video files it creates duplicate entries in the Frontend.
This is THE most annoying thing so far - why does it not clean out duplicates when you re-scan.. This is my highest priority.
When I rename a file so the Poster Art will work I end getting 2 entries.. I understand there are scripts you need to get. I not sure if there any for version 0.26 thanks to apt-get update I am on 0.26 and I wonder does anyone know of a script or method to clean out DEAD links in the database ... { why this is not automatic is beyond me }

4-I have multiple issues with the inbuilt player - I find VLC is the only player that seems to handle both video and sound correctly
I only wish I could preset the CROP/SUBTITLE setting on VLC files so I do not have to do it every time I watch a movie that needs to be re-sized.

Any comments would be appreciated.

---

### Post by PhilWig on 2013-04-06
I have a Hauppauge T500 but in the UK.  It's a really solid performer which works well with Myth.

It has an on-board 'low noise amplifier' (LNA) which can be turned on by software.  See this:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500#Forcing_the_activation_of_LNAs_.28Low_Noise_Amplifier.29](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500#Forcing_the_activation_of_LNAs_.28Low_Noise_Amplifier.29)

Note that
a)  Seemingly the filename required changed recently.  For 12.04 you need /etc/modprobe.d/options.conf, not /etc/modprobe.d/options
b)  Any changes (such as LNA) need a cold reboot to be accepted.  Power down and unplug system from wall socket for (say) 30 secs then boot up.

I would suggest splitting your antenna to both TV and Myth - there will be the odd occasion where you will want TV without Myth.

For general reception problems try my new hot off the press wiki [http://www.mythtv.org/wiki/DVB-T_Reception_Problems](http://www.mythtv.org/wiki/DVB-T_Reception_Problems)
Not properly indexed yet but might give a few pointers.

Don't give in with Myth too soon!  Best wishes
Phil

---

