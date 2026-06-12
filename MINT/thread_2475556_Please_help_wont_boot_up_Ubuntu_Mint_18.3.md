---
title: "Please help wont boot up Ubuntu Mint 18.3"
date: 2022-05-31
forum: MINT
---

### Post by aj2022 on 2022-05-31
Hi Community, I'm trying to help My Neighbour who has a computer that is running Ubuntu Mint and it came up with this error

When you turn on the PC it shows this error (Screenshot 1)[IMG]https://drive.google.com/file/d/1vI-V2vUIhzm2x9pSGZV6IauOCWRnYpEg/view?usp=sharing[/IMG][IMG]https://drive.google.com/file/d/1cVOxKZdZ5ftLai84p9avO7ukYWuA9TNQ/view?usp=sharing[/IMG]

and the I get this error (Screenshot 2)[IMG]https://drive.google.com/file/d/1vI-V2vUIhzm2x9pSGZV6IauOCWRnYpEg/view?usp=sharing[/IMG][IMG]https://drive.google.com/file/d/1cVOxKZdZ5ftLai84p9avO7ukYWuA9TNQ/view?usp=sharing[/IMG]
[IMG]https://drive.google.com/file/d/1vI-V2vUIhzm2x9pSGZV6IauOCWRnYpEg/view?usp=sharing[/IMG]

I have no idea what they mean.


The problem is there are a lot of work files on the system that are needed and not sure of what to do or how best to sort out, can anyone advise ?  

I have looked at creating a USB boot and then try and upload all the files to a cloud storage but im a bit confused, so if anyone here can help me i would really appreciate the help and advise

---

### Post by #&amp;thj^% on 2022-05-31
It's letting you know, you have to run a fdisk  against /dev/sda1
More here: [https://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/](https://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/)

---

### Post by guiverc on 2022-05-31
Be aware that there is no such thing as Ubuntu Mint; they are different OSes.

Ubuntu and *flavors* of Ubuntu (see [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) for the *flavors*) are built on the same Ubuntu infrastructure only using Ubuntu software, all of which are *runtime adjustment* free, as *developers* have upload privileges to the Ubuntu repositories.

Linux Mint is not a Ubuntu system, but a different system that is based on Ubuntu - thus has chosen to use *runtime adjustments* to deal with changes they like, given they don't have *upload* rights to Ubuntu repositories.  They also included 3rd party software Ubuntu doesn't use.

Also be aware [Linux Mint 18.3 is **end of life **and has been for over a year.]("https://blog.linuxmint.com/?p=3457")

---

### Post by TheFu on 2022-05-31
> **guiverc said:**
>  
Also be aware [Linux Mint 18.3 is **end of life **and has been for over a year.]("https://blog.linuxmint.com/?p=3457")

+1.
Please don't run unsupported OSes. It isn't bad just for you or the user, but the entire world, if they connect to the internet.

---

### Post by QIII on 2022-06-01
Moved to MINT.

And I will echo again what has been said:  Do not run an unsupported release of any OS.  And please avoid endangering everyone else by connecting it to the web.

---

### Post by yancek on 2022-06-01
The message in your second image specifically states to run fsck manually.  fsck is a filesystem check which any OS will have software to do.  Since you cannot boot the system you would need to use a bootable USB with a LInux system on it.  What  are you confused about?  There thousands of sites describing the process available online as well as a number of different applications you can use,  Do an online search for software to create a bootable linux usb and you should get a number of sites with options.  If Mint is the only OS on the computer, you will need to obviously use another to create it which you can do from either windows or Linux.j

---

### Post by mIk3_08 on 2022-06-01
> **aj2022 said:**
> Hi Community, I'm trying to help My Neighbour who has a computer that is running Ubuntu Mint and it came up with this error
When you turn on the PC it shows this error (Screenshot 1)[IMG]https://drive.google.com/file/d/1vI-V2vUIhzm2x9pSGZV6IauOCWRnYpEg/view?usp=sharing[/IMG][IMG]https://drive.google.com/file/d/1cVOxKZdZ5ftLai84p9avO7ukYWuA9TNQ/view?usp=sharing[/IMG]
and the I get this error (Screenshot 2)[IMG]https://drive.google.com/file/d/1vI-V2vUIhzm2x9pSGZV6IauOCWRnYpEg/view?usp=sharing[/IMG][IMG]https://drive.google.com/file/d/1cVOxKZdZ5ftLai84p9avO7ukYWuA9TNQ/view?usp=sharing[/IMG]
[IMG]https://drive.google.com/file/d/1vI-V2vUIhzm2x9pSGZV6IauOCWRnYpEg/view?usp=sharing[/IMG]
I have no idea what they mean.
The problem is there are a lot of work files on the system that are needed and not sure of what to do or how best to sort out, can anyone advise ?
I have looked at creating a USB boot and then try and upload all the files to a cloud storage but im a bit confused, so if anyone here can help me i would really appreciate the help and advise
You have made duplication of thread post. I agree with guiverc that "Be aware Linux Mint 18.3 is end of life and has been for over a year" But if you continue to use it, use it at your own risk and maybe fsck can still fix your system machine issue. Regards and cheers.

---

