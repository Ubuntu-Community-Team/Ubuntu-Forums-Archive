---
title: "Partitioning for dual boot"
date: 2009-07-01
forum: Mythbuntu
---

### Post by larsolav on 2009-07-01
Hi there!
I am about to build a bedroom Mythbuntu front end machine. I would like to install Windows 7 when it officially comes out later this year so that I have a dual boot machine. I have never created a dual boot machine before, so I am consulting the internet. Have found many guides for adding Ubuntu after Windows. 

I will try to follow these instructions: [https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")

Now, this weekend, when I install Mythbuntu, should I create a partition that is half the size of the hard drive on which I will install Mythbuntu, and then later I can install Windows 7 on the rest of the drive according to the instructions in the link above? 


By the way, I will be installing a [ZOTAC GF9300-D-E LGA 775 NVIDIA GeForce 9300 HDMI WiFi Mini ITX Intel Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813500022"). I haven't seen any posts here about this board, so I will share my experiences as soon as my system is built.

---

### Post by pro003 on 2009-07-01
> **larsolav said:**
> Hi there!
I am about to build a bedroom Mythbuntu front end machine. I would like to install Windows 7 when it officially comes out later this year so that I have a dual boot machine. I have never created a dual boot machine before, so I am consulting the internet. Have found many guides for adding Ubuntu after Windows. 

I will try to follow these instructions: [https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")

Now, this weekend, when I install Mythbuntu, should I create a partition that is half the size of the hard drive on which I will install Mythbuntu, and then later I can install Windows 7 on the rest of the drive according to the instructions in the link above? 


By the way, I will be installing a [ZOTAC GF9300-D-E LGA 775 NVIDIA GeForce 9300 HDMI WiFi Mini ITX Intel Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813500022"). I haven't seen any posts here about this board, so I will share my experiences as soon as my system is built.

As far as I'm concerned and what it used to be a 'normal procedure' is to first install your Windows OS and then install Ubuntu or any other Linux distro that you may happen to like. This is because of dual booting, it's much simplier than if you would install Ubuntu and then Windows, 'cause grub will be gone and you would be able to boot only into Windows. There are ways, but... since you're novice...

---

### Post by dsauter on 2009-07-01
I agree with pro003.  If you want to keep things simple, install Windows first, then Ubuntu.

My steps always include partitioning the disk with GParted Live CD.  I usually have at least 4 partitions.  One for Windows, one for Ubuntu, a large data partition (to be used by both OS's) and a swap file.  

Sometimes when I have space, I leave a 5th partition available in case I want to mess around with another linux (triple-boot).  This is especially nice with my Myth box (combined FE/BE).  I tend to upgrade my backend machine on this extra partition, and then cut over to the new partition when I'm sure it's working well.

---

### Post by larsolav on 2009-07-01
Thank you both pro003 and dsauter!
I will download Windows 7 RC today and install it before Mythbuntu.

dsauter, I'm not really keeping any media on this machine (at least I think) as it will mostly be a frontend only. Do you still recommend I first use GParted Live CD before installing Windows instead of using the Widows 7 partition shrinker?

---

### Post by dsauter on 2009-07-01
> **larsolav said:**
> Do you still recommend I first use GParted Live CD before installing Windows instead of using the Widows 7 partition shrinker?

I don't have any experience with Windows 7 partition shrinker.  I imagine it works fine and in combination with the ubuntu install partitioner that you'll run into anyway, I'm sure you'll be fine.

---

### Post by pro003 on 2009-07-01
am not sure you'll have an option to shrink ntfs partition when installing win7 unlike ubuntu that gives you this feature during install.
I would not use gparted in any ways cause every OS has its own ways of partitioning ... although ubuntu little bit more advanced :)

P.S there is a option in xp or vista when you can at some point press SHIFT+F10 and get into console and then do the partitioning with 'fdisk'

---

