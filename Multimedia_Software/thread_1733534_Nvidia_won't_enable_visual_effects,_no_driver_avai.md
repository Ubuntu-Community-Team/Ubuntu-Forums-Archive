---
title: "Nvidia won't enable visual effects, no driver available"
date: 2011-04-19
forum: Multimedia Software
---

### Post by marshall1001 on 2011-04-19
I've just finished my new build and installed Ubuntu 10.04 LTS.

I have in it an MSI N8400GS D512D3H (NVidia Geforce 8400GS) which I thought would work for Ubuntu. After installing Ubuntu the visual effects are disabled, can't even get "Normal" settings in the Appearance dialogue.

Updates have all been installed. Apt has been updated. "Hardware Drivers" screen draws a blank. No proprietary drivers listed at all.

First time I've actually used a Graphics Card in an Ubuntu install. Any advice?

---

### Post by ksprasad on 2011-04-19
Hi,

 You can try manually installing the driver.

1.  Download the latest driver from nvidia site.

2.  Press Ctrl+Alt+F1. It will lead you to terminal black screen. Login from there. 

3. sudo /etc/init.d/gdm stop

4. go to the directory where you downloaded the driver.

5. install it ./filename

6. sudo /etc/init.d/gdm start

Regards,
ksprasad

---

### Post by eddier on 2011-04-19
Go to menu,select "system" > "Administration" > "Additional Drivers",it should detect your NVidia card and install the drivers.

Or is that what you have already done ??:confused:

---

### Post by marshall1001 on 2011-04-19
> **eddier said:**
> Go to menu,select "system" > "Administration" > "Additional Drivers",it should detect your NVidia card and install the drivers.

Or is that what you have already done ??:confused:

If I'm correct the Additional Drivers screen is the newer version of the "hardware Drivers" screen.

I have already done this. At first a message box appears stating "Searching for available drivers" but nothing appears in the window.

After I've finished some work I'm going to attempt the fix outlined by ksprasad.

---

### Post by mikewhatever on 2011-04-19
This is odd. Open System->Administration->Software Sources and make sure the 'Proprietary drivers for devices' box is ticked. If the Hardware Drivers windows remains blanc after that, try installing the **nvidia-current** package, which is the driver for your card in 10.04.

PS: I'd strongly discourage installing the driver from nvidia.com manually, simply because you'll have to reinstall it after every kernel update (about once a month).

---

### Post by marshall1001 on 2011-04-21
> **mikewhatever said:**
> This is odd. Open System->Administration->Software Sources and make sure the 'Proprietary drivers for devices' box is ticked. If the Hardware Drivers windows remains blanc after that, try installing the **nvidia-current** package, which is the driver for your card in 10.04.

PS: I'd strongly discourage installing the driver from nvidia.com manually, simply because you'll have to reinstall it after every kernel update (about once a month).

Thank you.

I've ran apt-get on nvidia-current and it's doing its thing now. I'll mark thread as solved if it fixes the issue or run crying if it doesn't.

---

### Post by marshall1001 on 2011-04-21
This is me running and crying.

I installed the driver via apt-get as instructed. I checked back in "Hardware Drivers" and the driver was there and activated but I was still unable to change Visual Effects settings to "Normal" and the "Searching for Drivers" dialogue still appeared when trying to do so.

Upon restarting the machine my second monitor did not work and my resolution was dire. The Nvidia setting also asked em to edit xorg but did not instruct me as to how.

For now I've deactivated the driver and the system has returned to normal but I do feel like we're getting somewhere if anyone has any more ideas.

---

