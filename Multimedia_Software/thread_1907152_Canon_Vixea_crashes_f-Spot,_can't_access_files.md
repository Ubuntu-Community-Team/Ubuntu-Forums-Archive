---
title: "Canon Vixea crashes f-Spot, can't access files"
date: 2012-01-10
forum: Multimedia Software
---

### Post by seacoats on 2012-01-10
I'm new to Ubuntu, just switched from windoze to version 10.04.  My Canon Vixea HF M300 which worked fine on Windows XP now refuses to work.  It shows up on the desktop when i plug it in and prompts an auto-launch of f-Spot, which then crashes and makes me force quit.  If i don't launch f-Spot, and try and open the camera by clicking on it, i get a long delay and then the message

"Sorry, could not display all the contents of "Canon Video Camera": DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

Strangely, it once, after the long delay, allowed me to access the pictures on the camera without any trouble.  When that happened, i hadn't done anything differently, at least that i know of.

Thanks for the help!

---

### Post by wolfen69 on 2012-01-10
I would try Gthumb for your camera. I've had good luck with it.
```
sudo apt-get install gthumb
```

---

### Post by seacoats on 2012-01-17
Gthumb sort of works. It still gives me an error message, but allows access to photos on the camera if i chose Gthumb as the program to launch when the camera is plugged in. Iif i close that and go to the places-canon digital camera i get the error message...

Could not display "gphoto2://[usb:002,006]/".

Error: DBus error org.freedesktop.DBus.Error.ServiceUnknown: The name :1.198 was not provided by any .service files
Please select another viewer and try again.

---

### Post by seacoats on 2012-01-17
I can also get it to sometimes give me this error...

The folder contents could not be displayed.

Sorry, could not display all the contents of "Canon Video Camera": DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

A Google search of that dbus error gives me...
[http://www.multimediaboom.com/iphone-not-recognized-after-upgrading-ios-4-2-in-ubuntu-heres-how-to-solve-the-problem/](http://www.multimediaboom.com/iphone-not-recognized-after-upgrading-ios-4-2-in-ubuntu-heres-how-to-solve-the-problem/)

After more fiddling, it seems that if i chose Kino as the software to open the camera (Ubuntu doesn't seem to know how to view files on the camera on its own) and then close Kino, i'm able to then open the camera folders in the file viewer.  Any clue why this would be the case?  It seems really bizarre.

---

