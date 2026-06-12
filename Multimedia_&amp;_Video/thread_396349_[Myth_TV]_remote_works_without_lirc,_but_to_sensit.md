---
title: "[Myth TV] remote works without lirc, but to sensitive?"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by Junge on 2007-03-29
Hi there,

I've installed MythTV and it seems to work fine. The thing is I've got an RF MCE remote(made by X10) that seems to work automatically without Lirc. This means that MythTV responds when I press buttons. The problem is that the thing is to sensitive( e.g. if I scroll down it scrolls down two places) and that some buttons do other things than they should(e.g. volume down makes the volume go louder). 

I've tried to install Lirc, but when I do this the system just doesn't respond to the remote at all anymore. Not even with "irw". I've tried the modulese Lirc_Atiusb and Lirc_mceusb2, but with both it just does nothing anymore. When I uninstall Lirc it works exactly the same as before. 

This shouldn't be much of a problem when I know how I can adjust the sensitivity of the remote and adjust(and add) the commands of the buttons in MythTV, but I have no idea where I have to do that?

Anyone an idea?

Thnx in advance!

---

### Post by newlinux on 2007-03-29
normally in the ~/.lircrc file you would just adjust the "repeat" variable with each command. I'm not sure in your case even how your remote is working. I'm curious how about how yours is working and what it is using to map its buttons to IR commands...

---

### Post by Junge on 2007-03-29
> **newlinux said:**
> normally in the ~/.lircrc file you would just adjust the "repeat" variable with each command. I'm not sure in your case even how your remote is working. I'm curious how about how yours is working and what it is using to map its buttons to IR commands...

I tried to configure the key's in the myth frontend and when for example I press the "win button" on my remote MythTV sees it as the D from my keyboard. At least that's what I think, because when binding the key's there appears a D. While some other buttons it won't recognise?

Don't know if that's suppose to happen with Lirc, because that won't work with the drivers I used.

Gr.

Jeroen

---

### Post by newlinux on 2007-03-29
Mythfrontend button configuration maps keypresses to myth functions. LIRC maps remote control buttons to keypresses (e.g. it would map your win button to the keypress D). So if you aren't using LIRC, I wonder what is mapping your remote buttons to keypresses. The other buttons aren't recognized because there is nothing mapping them to a keypress. Whatever is mapping your remote buttons to keypresses doesn't have a mapping for them. So can you use irw now to see what keys you are pressing?

---

### Post by Junge on 2007-03-30
> **newlinux said:**
> Mythfrontend button configuration maps keypresses to myth functions. LIRC maps remote control buttons to keypresses (e.g. it would map your win button to the keypress D). So if you aren't using LIRC, I wonder what is mapping your remote buttons to keypresses. The other buttons aren't recognized because there is nothing mapping them to a keypress. Whatever is mapping your remote buttons to keypresses doesn't have a mapping for them. So can you use irw now to see what keys you are pressing?

No that's how I figure that Lirc doesn't work. When I run irw and start pressing key's on my remote nothing happens. While after I do 'make uninstall' there are things happening when I press buttons on the remote. 

This is the remote I have: [http://www.x10europe.com/pdf/OR22E-23E.pdf](http://www.x10europe.com/pdf/OR22E-23E.pdf) (it's the one on the right)

---

### Post by Junge on 2007-03-30
When I look in the device manager it sees the usb rf receiver as an X10 WTI RF receiver with the  capabilities: input, input.mouse, input.keyboard, button

Does someone know what this means?

---

### Post by newlinux on 2007-03-30
Hmm, accourding the gentoo wiki this remote can be controlled with kernel modules or LIRC, so yours is being controlled through kernel modules right now... IT also says if you are controlling it through the kernel module it won't work with LIRC, which probably explains why LIRC doesn't work for you. When you use the kernel module to control it I think you have less flexibility over the mapping of the buttons (what I saw on the net.  Can you use the arrow keys to control the mouse outside of myth?

what does:

```

lsmod | grep ati

```

return? how about:

```

lsmod | grep lirc

```

My knowledge is limited to configuring LIRC. I would recommend disabling the kernel module and then trying LIRC with atiusb module... But I'll look into it more...

---

