---
title: "No Lan connection at all"
date: 2013-02-16
forum: Networking &amp; Wireless
---

### Post by rveroo on 2013-02-16
using a gigabyte z77 d3h for my mother board which uses a Atheros GbE LAN chip. it says that the ethernet cable is not pluged in. Im guessing missing drivers or something any help would be nice thanks

---

### Post by magikarp555 on 2013-02-16
Don't know if this can help. I have Xubuntu so I can't help you directly but i found this in Xubuntu Offline Documentation: 

"Xubuntu supports a system known as **NDISWrapper**. This allows you to use a Windows wireless device driver under Xubuntu. To start using **NDISWrapper**:
                            
[LIST]
[*]                   Obtain the Windows driver for your network device and locate the file that ends with .inf
[*]                   Install the ndisgtk package
[*]                   Go to ** &#8594; System &#8594; Windows Wireless Drivers**
[*]                   Select **Install new driver**
[*]                   Choose the location of your Windows .inf file and click **Install**
[*]                   Click **OK**"
[/LIST]
So try to find Windows driver and install it with ndisgtk if it's supported by Lubuntu.

---

### Post by rveroo on 2013-02-16
> **magikarp555 said:**
> Don't know if this can help. I have Xubuntu so I can't help you directly but i found this in Xubuntu Offline Documentation: 

"Xubuntu supports a system known as **NDISWrapper**. This allows you to use a Windows wireless device driver under Xubuntu. To start using **NDISWrapper**:
                            
[LIST]
[*]                   Obtain the Windows driver for your network device and locate the file that ends with .inf
[*]                   Install the ndisgtk package
[*]                   Go to ** &#8594; System &#8594; Windows Wireless Drivers**
[*]                   Select **Install new driver**
[*]                   Choose the location of your Windows .inf file and click **Install**
[*]                   Click **OK**"
[/LIST]
So try to find Windows driver and install it with ndisgtk if it's supported by Lubuntu.
Ok but before i try this is for a wireless drivers, in trying to use the ethernet port on my motherboard so would it still work

---

### Post by magikarp555 on 2013-02-16
Sorry, didn't notice that its name is "Windows Wireless Drivers". Well you can still try to install it and make a try. Maybe it works anyway. Try and let me know.

---

### Post by Hadaka on 2013-02-16
Hi, here is a link that provides a couple other links that solved
the same kind of situation you are in..no network access wired
or wireless. I would suggest first running this command to verify
you have the same chip for your ethernet and wireless, seems you
will first need to get the wireless working to be able to load the
wired ethernet onboard chip.
```
lspci -nn | egrep '0200|0280' 
```

[http://ubuntuforums.org/showthread.php?p=12280344](http://ubuntuforums.org/showthread.php?p=12280344)

or you may want to just hang tight and hope chili555 sees this
post and can help you.

---

