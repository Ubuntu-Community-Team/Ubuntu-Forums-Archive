---
title: "Disabling autorun popup"
date: 2008-07-03
forum: Multimedia Software
---

### Post by joelparker on 2008-07-03
I wrote an autorun script on my usb drive. When I insert it, I have to acknowledge the security popup before it executes. I know this is for security reasons but is there a way to disable this popup on my own trusted computer. The issue is that the script I am trying to run needs to run on my server that doesn't always have a monitor,keyboard and mouse hooked up to it. So the desired behavior is to insert my usb drive and it executes my autorun script without hanging at a prompt.

---

### Post by pytheas22 on 2008-07-03
How did you write the script and in which language?  How does Ubuntu know to autorun it?  There would probably be a way to add in some conditional to the script saying not to run on a certain computer, which you could keep track of by any number of things (NIC MAC addresses, lspci entries, computer hostname...).

---

