---
title: "how to connect USB mobile modem to linux?"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by incrediblematt on 2009-11-27
Hello friends,

This linux newbie seeking help to connect a usb mobile modem to ubuntu.
I am using one of the indian telecom network, wanna to conenct my Mobile as modem to ubuntu to browse through the internet. 
I have already googled and tried some solutions, but no luck.
I read one solution which explained about the wvdial technique.
Let me brief you what i did.
I installed wvdial in our ubuntu.
then using gedit i tried to change the connection settings in the wvdial.config file
But sadly i was not able to save the .config file, though i am the admin for my system.
While saving the file it threw some "permission denied to save the file" error.
Neverthless, i tried to connect with the existing settings but no use.

Frineds, my question is why i am not able to save the wvdial.config file, though i have logged in as admin? Why ubuntu threw me such kinda permission error?
Please guide me through some good solutions to connect my USB mobile modem to our ubuntu.

Expecting your valuable replies.

Thanks in advance.

---

### Post by samigina on 2009-11-27
Linux stands on security so , the system will never leave you change files without prompt for permissions; to be sure you can edit the file just open it with the "sudo" command, the easiest way is to run a nautilus with "sudo nautilus" and then you will be like the Root user and will be able to do whatever you want. (dangerous thing).

One question: What mobile modem are you using? Theres plug and play support for many brands...

---

