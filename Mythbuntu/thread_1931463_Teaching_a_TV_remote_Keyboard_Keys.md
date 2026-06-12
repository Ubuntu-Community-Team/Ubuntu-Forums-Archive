---
title: "Teaching a TV remote Keyboard Keys"
date: 2012-02-25
forum: Mythbuntu
---

### Post by Dragonflyoh on 2012-02-25
I am looking for some help in teaching a learning TV remote keyboard key strokes. I recently installed 11.1 and my LIRC setup is not working. I have been working on the issue for a week and tried all sorts of fixes and the only thing I have accomplished is increasing my frustration level. I read on one of the MYTH sites that a large number of people have trained a learning remote keyboard keystrokes and they are happy with the results. I am looking for specifics like what brand of remote and wireless keyboard work. I have a GE Universal learning remote and a Microsoft keyboard and they pretty much ignore each other.
Any ideas/thoughts would be appreciated.
Jim

---

### Post by azmyth on 2012-02-27
Maybe I'm misunderstanding you but the keyboard needs a way to communicate with the PC either by IR (Lirc) or Wireless. If by wireless, then the keyboard commands defined in mythtv can be controlled with your wireless keyboard. If the keyboard sends IR signals then you will need lirc.

---

### Post by Dragonflyoh on 2012-02-28
My wireless keyboard works. What I have read is that people have used a learning remote control to learn the output of their keyboard and then use the remote in place of the keyboard. I am looking for what hardware was used to do that.

---

### Post by newlinux on 2012-02-28
Is you're keyboard an IR or RF or Bluetooth? Your  remote is probably IR so your keyboard would need to be IR. You would follow the instructions for your learning remote to read and learn the infrared keypresses from your keyboard into whatever corresponding key you want that to be on your remote. Then your keypresses on the remote would be interpreted by the IR receiver your keyboard uses with your computer. That would skip using LIRC. Alternatively if you are using a JP1 remote you could find the keyboad codes and program them in.

IR Keyboards are hard to come by these days, I used to have one and I accomplished what you are looking to do, but there were often quirks with the keypresses (the learning wasn't exact enough). It was a Solidtek ACK-571


[http://www.mythtv.org/wiki/Programming_Remotes_as_Keyboards](http://www.mythtv.org/wiki/Programming_Remotes_as_Keyboards) is a good place to start and has a couple of keyboard suggestions. I would recommend you try and get LIRC working though - it's a lot more flexible. I know you've had trobules but perhaps we can help...

---

### Post by klc5555 on 2012-02-28
> **azmyth said:**
> Maybe I'm misunderstanding you but the keyboard needs a way to communicate with the PC either by IR (Lirc) or Wireless. If by wireless, then the keyboard commands defined in mythtv can be controlled with your wireless keyboard. If the keyboard sends IR signals then you will need lirc.

IR remotes having dedicated USB IR receivers that are by default detected as USB keyboard devices, like the MCEUSB Vista remote or the discontinued Snapstream Firefly Mini (both of which I use on various machines) work through the USB keyboard module and don't require LIRC to function. Although they can also be set up to use LIRC as input devices in their own right on their own specialized kernel modules, if you really prefer. 

If used as simple USB keyboard devices, these IR remotes can have their extra keys mapped by using xmodmap to load the extra key mappings from a text file either at graphical shell startup or at the start of the "mythfrontend" script. Or you can reconfigure xkb to keep your remapping isolated just to specific apps, if you prefer.

---

### Post by LowSky on 2012-02-29
Just to be positive do you have an IR receiver attached to the PC?

If not you might want to pick up a Windows Media Center remote like this one: [http://www.newegg.com/Product/Product.aspx?Item=N82E16880101002](http://www.newegg.com/Product/Product.aspx?Item=N82E16880101002)
That remote is supported by Mythbuntu.

Then you can try to get your GE learning remote to pick up the codes.

---

### Post by Dragonflyoh on 2012-02-29
I have talked to keyboard and remote manufactures and the bottom line is the wireless keyboards use either bluetooth or RF and the remotes use IR  so learning the keyboard commands is not possible.

---

### Post by newlinux on 2012-02-29
> **Dragonflyoh said:**
> I have talked to keyboard and remote manufactures and the bottom line is the wireless keyboards use either bluetooth or RF and the remotes use IR  so learning the keyboard commands is not possible.

Well, not if you buy an IR keyboard as I mentioned in my post... But yeah, of course it won't work with RF or bluetooth.

---

### Post by Dragonflyoh on 2012-03-01
Thank you. I was mistaken in thinking IR keyboards were a thing of the past. My mistake. Now that I have seen the errors of my way I think I shall try a new remote. A IR keyboard would be as much $$ as a Rosewill RRC-126 Windows 7 Certified Media Center Infrared Remote Control so maybe that is the better path. Does the Rosewill work out of the box?

---

### Post by Dragonflyoh on 2012-03-06
Purchased the Rosewill remote and it worked out of the box. It was in a box not a shrink wrapped package. I used it to train my learning remote and all is great. Thanks for the assistance.

---

