---
title: "What is the lsusb command for Mandriva please?"
date: 2020-01-26
forum: Mandriva/Mageia
---

### Post by iamtheeggman2 on 2020-01-26
Hi,

The lusb command doesn't work in Mandriva, however, after some googling I cant seem to find it! I dont know if its my computer being 'helpful' by only listing ubuntu related stuff, but I cant believe its so difficult to find it? I am trying to use my usb camera on  mandriva n an old laptop but the webcam program cheese says no camera is detected.

---

### Post by ajgreeny on 2020-01-26
> **iamtheeggman2 said:**
> Hi,

The [COLOR="#FF0000"]lusb[/COLOR] command doesn't work in Mandriva, however, after some googling I cant seem to find it! I dont know if its my computer being 'helpful' by only listing ubuntu related stuff, but I cant believe its so difficult to find it? I am trying to use my usb camera on  mandriva n an old laptop but the webcam program cheese says no camera is detected.

I hope the [COLOR="#FF0000"]lusb[/COLOR] command you show in the text of your post is a typo and not the command you actually used; the real command is [COLOR="#FF0000"]lsusb[/COLOR] as you show in the title. 

Please show us the full output you get when running lsusb; just telling us that it doesn't work is unhelpful.
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

Can I also check that the camera really is a USB model and not attached by pci, as in a laptop.  What model is the camera?

---

### Post by iamtheeggman2 on 2020-02-01
> **ajgreeny said:**
> I hope the [COLOR=#FF0000]lusb[/COLOR] command you show in the text of your post is a typo and not the command you actually used; the real command is [COLOR=#FF0000]lsusb[/COLOR] as you show in the title. 

Please show us the full output you get when running lsusb; just telling us that it doesn't work is unhelpful.
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

Can I also check that the camera really is a USB model and not attached by pci, as in a laptop.  What model is the camera?

Ahh its funny you mention laptop, i was running mandriva on a laptop so does that make a difference? It is a usb camera conected to the usb port of the laptop. It was typed in correctly, yes it was a typo on my paragraph. 

Camera is 
[https://www.amazon.co.uk/COOCHEER-Waterproof-Borescope-Endoscope-Inspection/dp/B01CQQMXDM](https://www.amazon.co.uk/COOCHEER-Waterproof-Borescope-Endoscope-Inspection/dp/B01CQQMXDM)

---

### Post by iamtheeggman2 on 2020-02-01
On another note, why can linux see this micr sd card reader adapter but not show it up as an external device in gparted or file explorer?

Bus 001 Device 004: ID 14cd:8123 Super Top SD MMC Reader

---

### Post by deadflowr on 2020-02-01
> **iamtheeggman2 said:**
> On another note, why can linux see this micr sd card reader adapter but not show it up as an external device in gparted or file explorer?

Bus 001 Device 004: ID 14cd:8123 Super Top SD MMC Reader

Because a reader is not storage.

Edit: Why no storage attached to the reader is seen? Perhaps no driver, or improper settings or something.

---

