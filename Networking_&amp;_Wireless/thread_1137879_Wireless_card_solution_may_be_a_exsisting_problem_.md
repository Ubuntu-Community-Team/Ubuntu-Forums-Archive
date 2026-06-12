---
title: "Wireless card solution may be a exsisting problem for you"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by ckonestroh on 2009-04-26
[SIZE="3"]Acer Aspire 5520[/SIZE]

Now after following the steps in this link[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/]("http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/") which is a madwifi driver....

[COLOR="Red"][SIZE="4"]I found my problem ... Like most users on Ubuntu. I had tryed about 5 or 6 different times to load wireless card Atheros 5009 ar24x...[/SIZE][/COLOR] 

Major problem with so many attempts was there was never one manual on how to uninstall the drivers I had just loaded...

Luckly, I have a degree in Computer Science so finally I took a look at getting it to work objectively... I concluded after installing suse 11.1 that the wireless card was working... No problems with it loading in suse 11.1 first install....

after doing a make and a make install I came to step....
[SIZE="3"]
sudo gedit /etc/modules[/SIZE]

[SIZE="3"]
after opening this file I came to ndiswrapper was still trying to load wireless card and exsisted in this file twice.....   [COLOR="Red"]I removed both lines from the file did not insert ath_pci as recommend to see if Ubuntu would load the driver....[/COLOR]  Since it kept giving me Driver loaded ,but disabled at this time....

[COLOR="Blue"]Restarted my Ubuntu system after removing the two entries from /etc/modules...[/COLOR]


Wow it works....
n the normal course of events the modules we asked for when Linux was installed are loaded at boot time. To achieve this the file /etc/modules is used. This is a list of modules to be loaded


[SIZE="5"][COLOR="Lime"]Now I skipped a couple of problems I ran into[/COLOR][/SIZE] running the link above first off I don't have a 5006 Atheros  wifi card so in 

step 5 
5) Go into the newly created directory:

cd madwifi-hal-0.10.5.6-r3879-20081204

its telling me to change directory to madwifi-hal 0.10.5.6 r3879

the driver the madwifi website downloaded for me is madwifi-hal 0.10.5.6 r4000


Seeing is how my hardware in my Acer 5520 is not exactly the same chip set the file downloaded is different....

After doing a bit of investigation found that the /etc/modules is a folder that loades drivers that Ubuntu calls on when the kernel loads...
Keep in mind don't delete other files because some can point to hard drives and other hardware that loads based off those drivers....


Now the book definition is 

What are loadable modules
The Linux kernel can be extended to have more capabilities two basic ways:

    * Recompile the kernel with new capabilities "compiled-in" and reboot the new kernel
    * Build the kernel with loadable modules you might want occasionally. If you want a module's features to be added to your kernel, the the module can either automatically be loaded, or you can manually load it. When you are done using the module, you can either remove it from your kernel, or it can disappear automatically. 

Even after uninstalling ndiswrapper it didn't remove the lines from the

etc/modules configuration file...


Now I have never played with kernel so don't assume the file is removing itself from the configuration file.....[/SIZE]

---

