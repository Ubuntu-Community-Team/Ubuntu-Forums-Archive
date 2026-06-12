---
title: "Webcam shows pink and prey picture"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by R%&amp;92GH&amp; on 2007-12-02
hello

since I upgraded to 7.10, my webcam started showing a pink and grey image, and i'm not able to adjust the contrast, brightness, etc. Which I could using ubuntu 7.07, no matter what sofware i'm using (I have tried amsn and ekiga)

my device is the following:
```
Bus 002 Device 002: ID 0c45:613c Microdia 
```
And when I type dmesg:
```
[ 4159.144000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[ 4159.304000] usb 2-2: configuration #1 chosen from 1 choice
[ 4159.424000] Linux video capture interface: v2.00
[ 4159.480000] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.44
[ 4159.484000] usb 2-2: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613C)
[ 4159.512000] usb 2-2: HV7131R image sensor detected
[ 4159.884000] usb 2-2: Initialization succeeded
[ 4159.884000] usb 2-2: V4L2 device registered as /dev/video0
[ 4159.884000] usb 2-2: Optional device control through 'sysfs' interface disabled
[ 4159.884000] usbcore: registered new interface driver sn9c102
[ 4159.960000] usbcore: registered new interface driver gspca
[ 4159.960000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered

```

According to this website [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) I should use the spca5xx/LE driver, but ubuntu is automatically using the gspca. Maybe the problem is this, but I don't have any idea how to change the driver.

Do you think this is the problem? What was the driver that ubuntu 7.07 used?, because it worked pretty well with all programs and I could adjust all the image parameters.

I'll attach a picture sample to show how the webcam is working right now.

Thanks in advance

btw, the camera doesn't work in skype, people can only see a green square.

---

### Post by Matej_C. on 2007-12-18
I have almost the same problem, but my webcam shows grayscale.

I don't understand why, but first nothing except pipeline worked (system -->preferences -->multimedia settings - i'm not sure i is caled like this, i'm using different language--> video test)

then everything started to work, but in grayscale only (the thing above is the same)
the same it is in Windows xp (on the same computer)
my friend says thats because the driver, but i think that would not effect Windows

Has anyone an idea what does that mean?
i have emtec snake webcam if it helpes, thanks
[http://www.emtec-international.com/en/produit.php?categorie=AVNOM&gamme=AV%20WEBCAMS&ss_gamme=W1300SN]("http://www.emtec-international.com/en/produit.php?categorie=AVNOM&gamme=AV%20WEBCAMS&ss_gamme=W1300SN")

---

### Post by Matej_C. on 2007-12-21
i have a solution!!!!
do you have kopete?
it changes settings of your webcam, so run kopete an play with the settings of your webcam, change colour hue, so it will be ok

---

