---
title: "Ubuntu 11.10 - Dual monitor - Nvidia - Dual monitor stoped working when I upgraded"
date: 2011-10-22
forum: Multimedia Software
---

### Post by emanuel888 on 2011-10-22
When I upgraded my drivers with the recommended ones the second screen stoped working and the Display section of the system settings could not recognise the monitors.

I tried going back to the default one (it was installed with ubuntu) but it doesnt work either.

Is there a better way to fix my graphic drivers than "Add device section" in system settings?

* My card is a Nvidia GeForce 9400 GT

---

### Post by kommissario on 2011-10-23
go to the nvidia configuration 

there you should be able to enable the 2nd monitor

select twinview

and save the configuration

reboot

should work fine, I had the same issue with a similar graphic card and this was the solution for me

---

### Post by emanuel888 on 2011-10-23
Thank you very much, I did not realise there is a program coming with the driver installation.

Second screen works fine now :D

Next step for me will be play on linux :D

---

### Post by kommissario on 2011-10-23
np mate, 

you can now mark the theread as solved if all is ok for you

cheers

---

### Post by robertjastrow on 2011-10-23
kommissario said:

"go to the nvidia configuration"

Where is this?

This new 11.10 interface is horrible.

---

### Post by kommissario on 2011-10-23
we'll get used to it, is not so bad afterwards we'll forget the old one ...

just click the ubuntu icon at the top of the bar 

in the search field write nvidia ...

nvidia settings icon will appear, just click on it

---

### Post by MiD-AwE on 2011-12-04
For some reason nvidia configuration will not save. The error is 

Failed to parse existing X config file '/etc/X11/xorg.conf'!

what must I do?:confused:

---

### Post by zebull on 2011-12-05
Edit. (deleted)

---

### Post by zebull on 2011-12-05
> **MiD-AwE said:**
> For some reason nvidia configuration will not save. The error is 

Failed to parse existing X config file '/etc/X11/xorg.conf'!

what must I do?:confused:
Well.. Just click "OK" and ignore about "Failed" it will work anyway. Maybe you have to click "OK" once more. Don't know why this message appears.

---

### Post by MiD-AwE on 2011-12-05
> **zebull said:**
> Well.. Just click "OK" and ignore about "Failed" it will work anyway. Maybe you have to click "OK" once more. Don't know why this message appears.
Thank you. It works. I figured it out and it seems that the error is because there is no config file until you save one. :P

---

