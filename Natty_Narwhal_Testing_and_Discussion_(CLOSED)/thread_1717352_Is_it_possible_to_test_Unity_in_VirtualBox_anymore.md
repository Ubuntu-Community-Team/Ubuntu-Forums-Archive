---
title: "Is it possible to test Unity in VirtualBox anymore?"
date: 2011-03-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quadunit404 on 2011-03-29
So I've been trying - unsuccessfully - to get Unity running in VirtualBox since I don't feel like sticking in a thumb drive and rebooting each time I want to try to get used to it anymore for the past few days. Each time I try selecting Ubuntu (as in, Ubuntu + Compiz Unity) I get the Ubuntu Classic desktop without effects and Compiz throws up an error when I try running it in a terminal. I've reinstalled Ubuntu, tried different install CD images, and yet Compiz won't run, so therefore no Unity. Here's a screenshot of what I mean:

[IMG]http://i563.photobucket.com/albums/ss76/Quadunit404/CompizFAIL.png[/IMG]

I am pretty sure I enabled 3D acceleration in the Guest settings and installed the Guest Additions in VirtualBox.

And yes, I do know about Unity 2D, but that isn't ready for prime-time yet and last time I used it, while it was faster in a VM than Unity 3D, I didn't really enjoy using it that much.

btw: VirtualBox 4.0.4 on 64-bit Maverick host

---

### Post by Derspankster on 2011-03-29
Same issue here. It has put me off Unity since I haven't been able to test it at all.

---

### Post by MadCow108 on 2011-03-29
there was a problem with 3d support in vb being disabled by an update

try reinstalling virtualbox-ose-guest-x11 virtualbox-ose-guest-utils and virtualbox-ose-gues-dkms

---

### Post by Quadunit404 on 2011-03-29
Okay, trying that right now. I read on the VirtualBox forums that this was fixed in the VirtualBox SVN, but due to the rapidness of Natty's development cycle they haven't been able to keep up with all the changes done to it. And, of course, if you get VirtualBox from the SVN, you have to compile it, and I don't feel like waiting several hours for it to compile so...

EDIT: The solution posted above works. Setting to resolved now.

---

### Post by meanpt on 2011-03-30
I have all those installed and currently both 2d and 3d freeze, starting with the first click on the dash icon. For the time being I stopped testing them until some update solves it again.

---

### Post by IanW on 2011-03-30
meanpt - madcow108 recommended [COLOR="Red"]re[/COLOR]installing those packages to re-enable 3d.

---

### Post by inkFTW on 2011-03-30
> **MadCow108 said:**
> there was a problem with 3d support in vb being disabled by an update

try reinstalling virtualbox-ose-guest-x11 virtualbox-ose-guest-utils and virtualbox-ose-gues-dkms

I've tried reinstalling those packages and it gets me by the pixmap error but Unity still won't run.  Now I get:

Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
compiz (opengl) - Fatal: Support for non power of two textures missing
compiz (bailer) - Info: Ensuring a shell for your session
user@Natty:~$ Cannot register the panel shell: there is already one running.

Looks like it worked for Quadunit404 so maybe I'm just missing something.

---

### Post by Derspankster on 2011-04-02
It's just broke and will not likely get fixed any time soon. 11.04 will be final in 3 weeks. I don't blame the Virtualbox folks for not chasing their tails on this one. 

From what little bit I've seen of Unity I have no use for it anyway. I already own a Mac anyhow.

I see this thread is marked SOLVED. I must be missing something.

---

### Post by skrimpy on 2011-04-02
I'm also unable to get Unity to run properly in VirtualBox - I tried MadCow's suggestion, which does give me the Unity launcher.  Unfortunately it's there and gone again, there and gone again - flickers/blinks on and off over and over (the entire desktop is flickering/blinking).  This is basically unusable.  Same thing happens to me with Ubuntu Classic.

It does not happen in Ubuntu Classic with no effects.  I also have Unity 2D running okay.  

But no regular Unity/Compiz for this Natty Beta.  I have tried both 32-bit and 64-bit builds.  The build I have running successfuly with Unity 2D is the 32-bit.  The 64-bit is refusing to boot after installing guest additions.

---

### Post by Scoobin on 2011-04-02
I managed to get it working with the latest PPA version of VirtualBox (4.0.4) and the simple instructions here: [http://chrisblunt.com/2011/04/02/ubuntu-11-04-beta-how-to-test-unity-in-virtualbox-4/](http://chrisblunt.com/2011/04/02/ubuntu-11-04-beta-how-to-test-unity-in-virtualbox-4/)

I have also since managed to "break" Unity by playing with Compiz Advanced Settings Manager - I tried enabling Window Previews. All that I can see is a blank desktop with no gnome or Unity panels/launchers/menus/buttons.

---

### Post by Quadunit404 on 2011-04-02
> **Derspankster said:**
> I see this thread is marked SOLVED. I must be missing something.

It's solved because this was originally a support request for me and I marked it as solved since my issue was resolved.

I think you need a more high-end graphics card to run Unity in VirtualBox now, but seeing as to how I don't have a lower-end card than what I currently have...

---

### Post by Scoobin on 2011-04-03
Mine seems to be working again. Sometimes it would boot without a GUI and I would have to hit  CTRL + ALT + L and then click switch user and then try either Ubuntu or Ubuntu Classic from the login screen and it would work. It's going OK from what little testing I've done.

Now to test out Unity-2d. I wonder if that will break it. :D

---

### Post by skrimpy on 2011-04-04
So is the assumption that if the fixes proposed in this thread don't work, it's because of a low-end graphics card?  

I'm not too sure about that, because my machine has a very high-end card and I'm still having issues with the Unity launcher flickering on and off in 3D mode.  In addition, the LiveCD runs on my machine (host) without a hiccup.  It's just the guest that is having issues.

I am using an ATI card, maybe there's something else I'm missing in the Virtualbox settings or something else I need to add to my guest to get it working properly :(

---

### Post by skrimpy on 2011-04-04
I've gotten it running with Unity 3D now.  I redid the install using the daily build rather than the Beta... not sure what difference that would have made.

I'm still not getting 100% operation - the Unity launcher works elegantly enough, but I'm still getting my top "panel bar" degrading to an older theme.  In my themes it shows "custom theme" and I am unable to change it to Ambience/Radiance or any other themes.  It just goes back to the ugly "custom."  

Wondering if this is happening on everybody's Virtualbox install?

---

### Post by Scoobin on 2011-04-06
Nah mine is going fairly well. I've noticed some bugs, but the one I've reported is not related to it being a VM. Funnily enough, for me I can *only* get Unity to work in a VM. When I have booted the beta1 iso from a usb stick it would only load Gnome panels, even when I selected 'Ubuntu' from the login.

---

