---
title: "GUI not working"
date: 2013-06-26
forum: Multimedia Software
---

### Post by mankomal on 2013-06-26
Hello, 

I have recently loaded Ubuntu ver 12.10 desktop x86_64 on my machine which has 
Intel D525 processor 
2GbRAM, 
500GB HDD

The GUI screen is not working after 1 minute of load and hangs I am able to go to tty screen and work with command line but not use mouse on GUI please help 

regards

MS

---

### Post by Bucky Ball on 2013-06-26
*Thread moved to **Multimedia & Video**.*

Welcome to the forums. I am guessing this has something to do with your graphics card. If it proves otherwise will move to the appropriate sub-forum. ;)

Could you be a bit more specific, please? When you boot the machine, what happens? Do you get to a screen which gives you a list of the operating systems and kernels installed? If not, hit shift just after the BIOS screen when the computer boots and that should get you there.

Highlight the first entry on the list and type 'e'. That will let you edit the line. Look for the line that ends in 'quiet' or 'splash' or any combination of both. To the end of that add 'nomodset'. Follow the instructions at the bottom of the screen to save the changes and continue with boot.

Another option is when you get to the command line, what happens when you type:

startx

... and hit return? If you don't get to the desktop, post the exact message if you can. Did you try Ubuntu from the install disk first and did it work fine then?

---

### Post by mankomal on 2013-06-26
> **Bucky Ball said:**
> *Thread moved to **Multimedia & Video**.*

Welcome to the forums. I am guessing this has something to do with your graphics card. If it proves otherwise will move to the appropriate sub-forum. ;)
Thanks for prompt reply

> Could you be a bit more specific, please? When you boot the machine, what happens? Do you get to a screen which gives you a list of the operating systems and kernels installed? If not, hit shift just after the BIOS screen when the computer boots and that should get you there.
Everything works fine when i boot the machine, it lands directly to UBUNTU DESKTOP
No i dont get the screen which tells me list of OS or kernels installed
I tried to press shift , but nothing happened , just so that you know i have a USB keyboard & mouse installed and my machine is :
[http://axiomtek.com/products/ViewProduct.asp?view=913](http://axiomtek.com/products/ViewProduct.asp?view=913)


> Highlight the first entry on the list and type 'e'. That will let you edit the line. Look for the line that ends in 'quiet' or 'splash' or any combination of both. To the end of that add 'nomodset'. Follow the instructions at the bottom of the screen to save the changes and continue with boot.
I never reached the screen tried it twice so dont know about this yet ... still trying 

> Another option is when you get to the command line, what happens when you type:

startx

... and hit return? If you don't get to the desktop, post the exact message if you can. Did you try Ubuntu from the install disk first and did it work fine then?
I tried that on tty3 screen after my GUI hung up on me it shows just one UNTITLED folder no panel on top or left 

Furthermore, since the current restart the machine is working fine and GUI was working till I changed my display to Samsung 19"display ( TFT monitor)
after exactly 1 min the GUI disappeared with a black screen ...

I can still work on tty modes

---

### Post by Bucky Ball on 2013-06-26
When the machine is actually working and you are a desktop, do an update then check 'Additional Drivers'. Is there anything in there for your graphics card?

---

### Post by mankomal on 2013-07-02
> **Bucky Ball said:**
> When the machine is actually working and you are a desktop, do an update then check 'Additional Drivers'. Is there anything in there for your graphics card?

No there is nothing there for the graphic card

---

### Post by mankomal on 2013-07-02
> **Bucky Ball said:**
> *Thread moved to **Multimedia & Video**.*

Welcome to the forums. I am guessing this has something to do with your graphics card. If it proves otherwise will move to the appropriate sub-forum. ;)

Could you be a bit more specific, please? When you boot the machine, what happens? Do you get to a screen which gives you a list of the operating systems and kernels installed? If not, hit shift just after the BIOS screen when the computer boots and that should get you there.

Highlight the first entry on the list and type 'e'. That will let you edit the line. Look for the line that ends in 'quiet' or 'splash' or any combination of both. To the end of that add 'nomodset'. Follow the instructions at the bottom of the screen to save the changes and continue with boot.

Another option is when you get to the command line, what happens when you type:

startx

... and hit return? If you don't get to the desktop, post the exact message if you can. Did you try Ubuntu from the install disk first and did it work fine then?

Also I was able to enter the GNU GRUB page by pressing shift key, I entered  no modest after : 
linux        /boot/lmlinuz-3.5.0-17-generic root=UUID=32514556-e501-42e9-9c2b-68123fcdda5a ro    quiet splash\
$vt_handoff

in options below i have TAB to complete command, Ctrl-x or F10 to boot, ctrl-c or f2 for a command line or ESC to discard changes 
i have no option to save this so I pressed f10 and still there is a problem 
Please advise what should i do ?
I dont get any error message or anything 
even when i try to run startx from terminal screen 
but when i run startx from terminal screen it only shows me an untitled folder and no top or side bar/toolbar

---

### Post by Bucky Ball on 2013-07-02
When you get to that desktop, what is in the folder and what happens when you right click on the desktop?

---

### Post by mankomal on 2013-07-03
> **Bucky Ball said:**
> When you get to that desktop, what is in the folder and what happens when you right click on the desktop?

the folder is empty but I can see on the left computer, home, desktop .... TABS
when I right click I get options : 
create new folder
create new document (with sub-options)
organize desktop by name 
keep Aligned ( checked) 
paste (disabled)
change desktop background

---

### Post by Bucky Ball on 2013-07-03
So computer, home are there on the desktop, present and correct? If you click them they have the correct data? I'm presuming this is Unity. Did it work okay when you tried it from the install CD, if you did?

I'd be tempted to try a known solid release like 12.04 LTS to make sure it is not something in the version. If it happens with 12.04 as well then it gives a clue. Perhaps you could try them both from the install disk and see if they both work okay there.

---

### Post by mankomal on 2013-07-03
> **Bucky Ball said:**
> So computer, home are there on the desktop, present and correct? If you click them they have the correct data? I'm presuming this is Unity. Did it work okay when you tried it from the install CD, if you did?

I'd be tempted to try a known solid release like 12.04 LTS to make sure it is not something in the version. If it happens with 12.04 as well then it gives a clue. Perhaps you could try them both from the install disk and see if they both work okay there.

no computer home etc etc are visible when i open the folder (UNTITLED FOLDER) I dont see anything other than that in startx
I installed this from USB key ver is 12.04LTS
it says on terminal screen Ubuntu 12.10 (GNU/Linux 3.5.0-17-generic x86_64)

---

### Post by mankomal on 2013-07-03
> **mankomal said:**
> no computer home etc etc are visible when i open the folder (UNTITLED FOLDER) I dont see anything other than that in startx
I installed this from USB key ver is 12.04LTS
it says on terminal screen Ubuntu 12.10 (GNU/Linux 3.5.0-17-generic x86_64)

OK I just installed UBUNTU on one more machine which has Xeon 3.2 processor and 2 Gb RAM 
till now there is no problem i am facing on that machine 
also it is able to detect my Samsung 19"display which the earlier Atom machine is not able to... 
Why is that

---

### Post by Bucky Ball on 2013-07-03
The machine you're having issues with:

> **mankomal]I have recently loaded Ubuntu ver 12.10 desktop x86_64 on my machine which has
Intel D525 processor
2GbRAM,
500GB HDD[/QUOTE]

Please post a thread in ***Multimedia & Video*** regarding why the Atom does not pick up your monitor. It is off topic. Thanks.  said:**
> ... it is able to detect my Samsung 19"display which the earlier Atom machine is not able to...
Why is that?

---

### Post by mankomal on 2013-07-03
> **Bucky Ball said:**
> The machine you're having issues with:



Please post a thread in ***Multimedia & Video*** regarding why the Atom does not pick up your monitor. It is off topic. Thanks. ;)


Ok Doing this now , closing this thread

---

### Post by Bucky Ball on 2013-07-03
Post a link to it here if you like. I will leave this thread open in case there is input regarding your original issue. ;)

---

### Post by mankomal on 2013-07-03
> **Bucky Ball said:**
> Post a link to it here if you like. I will leave this thread open in case there is input regarding your original issue. ;)

Thanks Bucky 
I have posted a new thread here 
[http://ubuntuforums.org/showthread.php?t=2159415&p=12715881](http://ubuntuforums.org/showthread.php?t=2159415&p=12715881)
I suspect this could be the issue let see if we are able to solve it

---

