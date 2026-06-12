---
title: "Why Maverick is still not recognizing my motorola v3m mobile phone?"
date: 2010-06-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-06-25
When i connect my mobile i get in the mobile a message "connected  as usb files in the memory card are not available now."
it's a bit annoying when i want to use my phone as a camera and upload images from it to the Internet.

Thanks in advance.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598757](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598757)

---

### Post by philinux on 2010-06-25
> **aviramof said:**
> When i connect my mobile i get in the mobile a message "connected  as usb files in the memory card are not available now."
it's a bit annoying when i want to use my phone as a camera and upload images from it to the Internet.

Thanks in advance.

Does it work with lucid lynx?

---

### Post by aviramof on 2010-06-25
No it didn't maybe it worked with intrepid but i don't remember because i didn't used it for enaf time to remember it.

---

### Post by philinux on 2010-06-25
> **aviramof said:**
> No it didn't maybe it worked with intrepid but i don't remember because i didn't used it for enaf time to remember it.

Found this with google.
[https://answers.launchpad.net/ubuntu/+source/hal/+question/13398](https://answers.launchpad.net/ubuntu/+source/hal/+question/13398)

[edit] apt-cache policy moto4lin
moto4lin:
  Installed: (none)
  Candidate: 0.3+svn20071228-1
  Version table:
     0.3+svn20071228-1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Packages

---

### Post by aviramof on 2010-06-25
I did tried several softwares in the past with no luck is there any ls command or something that can show me if ubuntu even recognize something?

moto4lin don't recognize it too.

---

### Post by aviramof on 2010-06-25
i just checked sudo moto4lin and it detect my mobile as 05c6 1000 qualcomm, incorparated.

[http://moto4lin.sourceforge.net/wiki/Razr_V3m](http://moto4lin.sourceforge.net/wiki/Razr_V3m)

---

### Post by TerminX on 2010-06-25
That phone is old enough to still have a settings menu toggle between USB serial interface and USB mass storage, isn't it?  You might want to verify that's set correctly.

---

### Post by aviramof on 2010-06-26
I checked the phone setting and it's fine it's ubuntu that doesn't support it as it said here:
[http://moto4lin.sourceforge.net/wiki/Razr_V3m](http://moto4lin.sourceforge.net/wiki/Razr_V3m)

"**Does not currently seem to be supported**, along with its brother [ V3c]("http://moto4lin.sourceforge.net/wiki/Razr_V3c")."

---

### Post by ranch hand on 2010-06-26
It could, possibly, be that 10.10 is under heavy development right now and that this is not a priority at this point.

There really is a reason why there are several notices that this OS should not be used as a production OS.  One of the main reasons is that it does not, and is not at this time intended to, work in a lot of ways.

Relax, enjoy the ride, unknot your knickers, have FUN.

---

### Post by aviramof on 2010-06-26
Would you mind check a little better before you reply?

It also didn't worked in lucid as i said in reply #3 and also i gave a link to a site that
said that Ubuntu doesn't support v3m at all.

[http://moto4lin.sourceforge.net/wiki/Razr_V3m](http://moto4lin.sourceforge.net/wiki/Razr_V3m)

Which mean that it something that should have been fixed long ago.

---

### Post by ranch hand on 2010-06-26
Well, they may fix it in 10.10.  I wouldn't expect it yet but I haven't looked for it in the blueprint either.

10.04 is its own problem.

I do not have and never have had a cell phone.  So I am no expert on this problem.  That said, is there a bug filed for 10.04?  Is there a bug filed for 10.10?  If not there is little chance of a fix.  If no one else verifies that it is a problem on the filed bugs, if they exist, there is little chance of anything happening.

You will just have to ride it out.

I do not even know how important this is.  Why would you need this for?  How do you connect the phone and the box?

My land line phone gets by quite well without any connection with my box not sure I even like the idea of connecting them.  Sounds like a security hole to me.

---

### Post by aviramof on 2010-06-26
In the 21th century everything is connected to something eles and my phone is nothing compare to the new iphones and etc you really need
to start checking what you can do today with a good moblie phone.

Any way in my case i connect my phone to the computer with usb-mini usb cable and i use my phone as a storage place i have 2 GB 
memory card there in newer phones it can reach up to 30GB i store there files like pictures and music that i can see and play in the mobile 
phone and i also use it as a camera and transfer this pictures to the computer so i can upload them to where ever i want and like i said
it's nothing compare to all the other applications and etc that new phones use today and can be added change or replace by connecting the
mobile to the computer.

Just to conclude say i want to post bug report on the matter i need to know what package 
i need to write the report about is it the kernel itself? or is it something eles?

Thanks in advance.

---

### Post by philinux on 2010-06-26
In this case I would do this.

```
ubuntu-bug linux
```

---

### Post by aviramof on 2010-06-26
Ok i did it i'm not sure that i did it right but i hope that it would be ok.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598757](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598757)

---

### Post by ranch hand on 2010-06-26
Well I can see that connecting to your box is pretty basic to the function of the phone.  Kind of neat.

Were there bugs filed that came up as options when you filed yours?  Just wondering how widespread this is.

Hope it gets fixed for you.

---

### Post by aviramof on 2010-06-27
If anyone here have a v3m moble phone please reply in this bug report.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598757](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598757)

---

