---
title: "Wireless Never Works !*#?!"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by DaMad-Man on 2010-01-29
I am fed up with Linux never being consistent with WIRELESS ](*,):twisted:!!! ([http://www.merriam-webster.com/netdict/consistent](http://www.merriam-webster.com/netdict/consistent)) Here's what I want to do...  How would I go about getting [COLOR=Red]ALL[/COLOR] wireless drivers??? Or if that would be to much data, all old school ([COLOR=Red]Legacy[/COLOR]) wireless? Also How can U get CENI-cli (iF i HAVE TO COMPILE THE THING TO WORK I WILL - Just point me in the right direction)? The reason for this is when I wanta try a new distro, wireless never works on my old school desktop (Wireless Desktop), so I have to diconect 2 desktops, travel from room to room reconnect 1 & get what I need then disconnect, then reconnect 2 desktops. The same when I try on either laptop except all I have to do is connect an extra wire in the router. MAN the HELL with that ](*,):twisted:!!! I need something that I can easily access @ all times, any time, off-line (usb, cd, dvd, etc...). (I already gksu nautilus and copy my personal wireless info from lib & usr to the root and reboot with no problem, but it doesn't work on everything) I would like to remaster Ubuntu with all these in there and distribute to my people. So they won't have to go through what I have gone through for the last 9 months ](*,):twisted:!!! And I know others would like an answer to this as well. So on behalf of me, and all others who are tired of packing equipment around, I will say this in advance. Your knowledge, wisdom, & enlightenment, is well _***[COLOR=Red]APPRECIATED[/COLOR]***_

---

### Post by zipperback on 2010-01-29
> **DaMad-Man said:**
> I am fed up with Linux never being consistent with WIRELESS 

What kind of wireless card do you have?

Could you please explain what kind of problems you are having?
What are the errors that you are experiencing?

Open a terminal window with Applications &#8594; Accessories &#8594; Terminal

Then enter the following commands and post the results back here.

```

lsusb

```

```

lspci

```

That will give us a little more information about the hardware in your computer.

> **DaMad-Man said:**
> 
Here's what I want to do...  How would I go about getting [COLOR=Red]ALL[/COLOR] wireless drivers??? 

You don't need all the wireless drivers. You just need the correct ones for your system. 
The information that I requested above will tell us what kind of hardware is being recognized by your computer.


> **DaMad-Man said:**
> 
Also How can U get CENI-cli (iF i HAVE TO COMPILE THE THING TO WORK I WILL - Just point me in the right direction)?

Huh? Please clarify what you want.

> **DaMad-Man said:**
> I would like to remaster Ubuntu with all these in there and distribute to my people. So they won't have to go through what I have gone through for the last 9 months ](*,):twisted:!!! And I know others would like an answer to this as well. So on behalf of me, and all others who are tired of packing equipment around, I will say this in advance. Your knowledge, wisdom, & enlightenment, is well 

If it's a common chipset for your wireless card, then it should be pretty simple for us to help you get it working. There isn't any reason to remaster Ubuntu just for your wifi card, you just need to setup the correct driver.  Please provide the output from the two commands I listed above. Thank you.

Zipperback
:popcorn:

---

### Post by DaMad-Man on 2010-01-29
[QUOTE=zipperback;8743254]What kind of wireless card do you have?

Could you please explain what kind of problems you are having?
What are the errors that you are experiencing?

I want [COLOR=Red]All[/COLOR] wireless (How would I achieve this?). I rebuild computers, I always run into different problems with different equipment, hence the need to remaster Ubuntu for different machines [COLOR=Red]ALL[/COLOR] wireless drivers, not just mine if that was unclear. I can fix my own problems with a wired connection. I dislike breaking down a computer just to get wireless working in 1Min. then rehook the computers back up.

     Quote:
                                                                      Originally Posted by **DaMad-Man**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8743016#post8743016")                 
                 *Also How can U get CENI-cli (iF i HAVE TO COMPILE THE THING TO WORK I WILL - Just point me in the right direction)?*
                                 
Huh? Please clarify what you want.

CENI - is a command line input for wireless I use on SIDUX. U can backport this from Hardy I think. I did it once before in 9.04 but do not remember the details. I know I can go there (to SIDUX) and ask but since I'm here and I know it works, I asked here because one of U GURU's might have or still use it. I would like to be able to install Ubuntu without dissembling my equipment to do this... In my post I'm sure I mentioned @ least 3 different computers?

---

### Post by DaMad-Man on 2010-01-29
Let's see if I can make this simpler. I explained the problem in the 1st post. This is the solution I am looking for. How would I go about obtaining [COLOR=Red]ALL[/COLOR] Wireless Drivers (Forget about size). [COLOR=Red]ALL[/COLOR] - as in The first one they ever made to the most recent one in 2010. So I could just pop in that usb, cd, or dvd after install if, Ubuntu doesn't see the Wireless... The main thing I am trying to achieve is ***_[COLOR=Red]OFF-LINE[/COLOR]_*** - Get The Wireless Working. Reboot, then download whatever update that computer needs.....

Jockey - The thing that finds the hardware. On DVD, now that would be kool, but just filled up with wireless drivers....

No internet connection, but still able to connect to my [COLOR=Red]HOME NETWORK[/COLOR]... That would be beautiful....

I simply need to be able to connect without a [COLOR=Red]WIRED[/COLOR] connection.....

Power Goes Out: 2 Laptops could speak to each other after install without ever needing an internet connect to download the driver...
 
Is it becoming clearer yet???

[COLOR=Red]ALL DRIVERS 
 ~UBUNTU~[/COLOR]

---

### Post by DaMad-Man on 2010-02-02
It's Been 3 days & I've been out of town. U meen to tell me no one has any idea how to do this? Or did I hurt someone's feelings? I need [COLOR=Red]ALL[/COLOR] Wireless drivers ([COLOR=Red]ALL[/COLOR]- As In Every last One). Any Clues??? If this is a very difficult task for the GURU's of the mighty Buntu. Please direct me to the place I need to go to achieve this to me, simple task. As I am only 9 months into Linux and by far Ubuntu is the best thus far to me...... It just seems to work on every machine I have come in contact with so far... I need real help, but if I can't relieve-ate the problem it is of no real use. Just a toy...

---

