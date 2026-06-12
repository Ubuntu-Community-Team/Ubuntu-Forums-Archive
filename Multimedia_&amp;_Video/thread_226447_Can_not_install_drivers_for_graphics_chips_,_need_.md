---
title: "Can not install drivers for graphics chips , need help!"
date: 2006-07-31
forum: Multimedia &amp; Video
---

### Post by vastsky on 2006-07-31
Hello.Friends!

The refresh rate of my CRT is 60Hz, and I found that the driver for grahic chip is not installed. So I search by Google and I did find a driver for it luckily.

And after I download the driver, I find some problems during installing.
The instrucions are:
> 
---------------------------------------------------------------------------
Building and loading viafb device driver for Linux kernel 2.6
---------------------------------------------------------------------------
Building fbcon console module.
    Step 1: Change to folder /usr/src/linux-2.6.
            # cd /usr/src/linux-2.6.
              The linux-2.6 directory depend on your kernel version, so if your kernel version is
              2.6.5-1.358, you should type "/usr/src/linux-2.6.5-1.358".
    Step 2: Configuring the kernel module
            # make menuconfig
    Step 3: Select fbcon item to module.
            -> Device Drivers->Graphics support->Console display driver support->
               <M> Framebuffer Console support
    Step 4: Save the current setting and quit.
    Step 5: Make fbcon module.
            # make modules
              Note that if no any error, this step will be produced "fbcon.ko" in 
              /usr/src/linux-2.6./drivers/video/console folder.
    Step 6: Copy fbcon.ko to lib folder.
            # cp /usr/src/linux-2.6./drivers/video/console/fbcon.ko  \
              /lib/modules/2.6./kernel/drivers/video

---------------------------------------------------------------------------
Building viafb as a module. (for Linux kernel 2.6)
    Make sure you have the kernel sources in /usr/src/linux-2.6.
    Change to the viafb directory, and then following below steps:
    
    Step 1: change to folder /usr/src/linux-2.6.
            # cd /usr/src/linux-2.6.
              The linux-2.6 directory depend on your kernel version, so if your kernel version is
              2.6.5-1.358, you should type "/usr/src/linux-2.6.5-1.358".
    Step 2: copy viafb folder in current directory.
            # cp -rf .../viafb ./
    Step 3: change to viafb directory
            # cd /viafb
    Step 4: Clear all object file.
            # make clean
    Step 5: Make source code
            # make
              Note that if no any error, this step will be produced an object file "viafb.ko".
    Step 6: Install viafb.ko framebuffer driver
            # make install

---------------------------------------------------------------------------
Using the viafb module. (for Linux kernel 2.6)
    If you want to modprobe viafb.ko into kernel and change the display mode in Linux kernel 2.6 and later versions,
    you need a framebuffer device driver(viafb.ko) and a framebuffer console module(fbcon.ko).
    Modprobing viafb will not change the display mode until you modprobe fbcon.
    You can see the related steps below.

    Step 1: Start viafb with default settings.
            # modprobe viafb
              Note that you can see the other options from "Using the viafb module. (for Linux kernel 2.4)" section.
    Step 2: Modprope fbcon.
            # modprobe fbcon

However, in the very beginning, things goes wrong. I can't find any folders in /usr/src/ ,what should I do?
I use *uname -r*to know my kernel version is 2.6.15-23-386, should I creat a folder like this */usr/src/2.6.15-23-386*?
From another book, I know */usr/src*is very important, becaurse it is related to the kernel. So I'd like to ask some advice instead of try myself.

So, friends. What should I do exactly.
Could you please give me some specified instructions, as I am a new born to 
Linux and Ubuntu.

ps: I use Ubuntu606LTS, and my graphic chip is *Integrated VIA UniChrome Pro Integrated Graphics Processor *with P4M800CE.

Thanks for reading!

---

### Post by cyclister on 2006-07-31
Do you have configurated higher receptories, in your repos list?
If not reach higher receptories first more package will appear in synaptic list.

Test upgrade your kernel image to i586 or even higher in synaptic, the nearest your hardware configuration the better, for a smooth stable run and nice applikations like all kinds of drivers.
In synaptic:
Search for image
Search for drivers choose a grafic driver for a via intelchip think I saw one when I was looking.You can test diffrent one and choose the one that suit your system best.

A thing with drivers they work little funny my geforce 3 does run best in firefox with woodo 3 drivers little odd.

Hope you get it togheter

---

### Post by vastsky on 2006-08-02
> **cyclister said:**
> Do you have configurated higher receptories, in your repos list?
If not reach higher receptories first more package will appear in synaptic list.

Test upgrade your kernel image to i586 or even higher in synaptic, the nearest your hardware configuration the better, for a smooth stable run and nice applikations like all kinds of drivers.
In synaptic:
Search for image
Search for drivers choose a grafic driver for a via intelchip think I saw one when I was looking.You can test diffrent one and choose the one that suit your system best.

A thing with drivers they work little funny my geforce 3 does run best in firefox with woodo 3 drivers little odd.

Hope you get it togheter

Thank You!
But i can't search any drivers in synaptic. 
Could anyone else can give me some advice to install the driver up?

---

### Post by cyclister on 2006-08-08
> **vastsky said:**
> Thank You!
But i can't search any drivers in synaptic. 
Could anyone else can give me some advice to install the driver up?

Sorry didnt see your post until now, you have to reach higher receptories.
You have a whole section of this, its not much.
Put in pack gcc- 3.4 first from synaptic or aptitude in terminal.
Then in terminal you write:
sudo cp/etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
(hope I spelld right here)
Then you have the recptories list you have to configure, only a couple of lines.Or this I have
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

You simply remove the whole list beneath Dapper Drake 6.06 or what you have for kernel, I think dapper look very nice.You do not eat only with your mouth most of the taste are acctully smell and see something all most every day that look dull arent so fun.

Then you might want to have a nice firewall or something else that suite's you.Then one day you might notice taht you do not have to have all that unnecessary package, but thats another story.

Best wishes on you path in the world of unix, linux system

---

