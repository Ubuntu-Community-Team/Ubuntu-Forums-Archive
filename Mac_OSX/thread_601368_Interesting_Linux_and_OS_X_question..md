---
title: "Interesting Linux and OS X question."
date: 2007-11-03
forum: Mac OSX
---

### Post by khurrum1990 on 2007-11-03
How is it that Mac OS X running on top of BSD is able to standby and hibernate properly while Linux which is a Unix clone can't? Why can't we make something like them?

---

### Post by b9anders on 2007-11-03
because OS X is configured to a very limited set of hardware - whereas Linux has hardware compatability for a huge range of hardware.

standby and hibernate works fine on my laptop for example. If linux were focused on only providing compatability with macs as OS X is, if would be just as efficient in these areas.

---

### Post by ddrichardson on 2007-11-03
> **khurrum1990 said:**
> How is it that Mac OS X running on top of BSD is able to standby and hibernate properly while Linux which is a Unix clone can't? Why can't we make something like them?That's a very inflammatory question. There is a limited amount of hardware that OSX runs on and Linux runs on a wide range of different system configurations, if in your experience you have had difficulty with APM, I'm terribly sorry but it is simply down to the huge variation in BIOS implementation on many different manufacturers - some have problems.

---

### Post by aysiu on 2007-11-03
See if you can pick up a used Dell Inspiron 500m.

Suspend and resume from suspend work perfectly out of the box with Ubuntu 7.04 and 7.10.

---

### Post by Alfa989 on 2007-11-03
> **b9anders said:**
> because OS X is configured to a very limited set of hardware - whereas Linux has hardware compatability for a huge range of hardware.
Well, this is just not true...

Tiger had to run on hundreds of different hardware configuration, each with its unique set of parts... Which, is impossible to test...

---

### Post by khurrum1990 on 2007-11-03
> **Alfa989 said:**
> Well, this is just not true...

Tiger had to run on hundreds of different hardware configuration, each with its unique set of parts... Which, is impossible to test...

Hi, yeah u could be right cause thats what I think. Mac's have got some similar hardware as other laptops as well sometimes even if u install Linux on a Macbook with all the drivers still suspend and resume don't work. 

Even though I fixed it on my computer and laptop I still think kernel developers should check out what Apple has done to make it work. If Linux wants to become the best OS in the market then this is one feature they really need to fix.

---

### Post by Alfa989 on 2007-11-04
> **khurrum1990 said:**
> Hi, yeah u could be right cause thats what I think. Mac's have got some similar hardware as other laptops as well sometimes even if u install Linux on a Macbook with all the drivers still suspend and resume don't work. 

Even though I fixed it on my computer and laptop I still think kernel developers should check out what Apple has done to make it work. If Linux wants to become the best OS in the market then this is one feature they really need to fix.
Agreed!

---

### Post by khurrum1990 on 2007-11-04
Seriously does anyone have any idea about how OS X suspends and hibernates? I would check it out myself but I have given my Mac to my brother these days. Any idea on how like the settings r and stuff on OS X for suspend and hibernate.

---

### Post by Demio on 2007-11-04
I don't know what suspend or hibernate means.

In Macs you normally put your computer to sleep, which means that all peripherals will be turned off and  all the internal components will be turned off  except for the RAM which will continue to be powered. And also, the OS goes into a suspended state or whatnot. When you retrun from sleep, it takes 2 or 3 seconds and you get back to the same state your computer was in when it went into sleep (except sometimes the network adapters which are still obtaining IPs).

---

### Post by localzuk on 2007-11-04
Well, hibernate does not work in Tiger on any desktop machines - it is restricted to laptops only.

And as others have said - Linux has to support many thousands of configurations of hardware, whereas OS X does not. Ok, it has multiple configurations of CPU/Graphics etc... but the underlying components that control power functions (the BIOS etc...) are controlled and limited in numbers. This means that they only need to develop it to work with those few.

An example of BIOS differences - I work in a school with 190 computers in use, and between then there are roughly 30 different motherboards, with their BIOS's etc...

Anyway, hibernate works perfectly on my cheap and cheerful desktop here...

---

### Post by Demio on 2007-11-04
It works if you enable it (through a hack), but sleep on a desktop machine is useless.

---

### Post by khurrum1990 on 2007-11-04
Hi, we r not really discussing whether something is useless or useful. For me if something doesn't work on my system, it just starts pissing me off. OS X whether or not it works with little hardware or not, it still works. We can make it work on Linux and it should work. Kernel developers should really develop a more efficient system for suspend to ram and disk. At least then u will be able to tell people that Linux works perfect.

Linux distributions like Ubuntu, Opensuse, Redhat should go tell companies, look here is the deal, any one using Linux is still using ur hardware and is still ur customer so make drivers that actually work just like they do for Windows.
What do u all think?

---

### Post by ddrichardson on 2007-11-04
I think you are working on a flawed premise in that, as I understand it, OSX is developed on BSD and not Linux.

That aside, Opensuse aren't telling anyone anything although Suse Enterprise might, same with RH - they're core business is the server market. No one is really making any money yet in the desktop market for the simple reason that there are so many free alternatives, such as Ubuntu.

It also doesn't make sense for them to demand companies make drivers, because as the people behind the product it's in their interests and not yet the manufacturers. The way ahead would be for these companies to devote some of their own resources into dedicated driver development - muxh as Novell have done, except in userspace (where the majority of devices people need to get working are) rather than kernel space. However, as long as we have the situation where kernel updates change fundamental names and each kernel breaks at least some current drivers this situation is a little up in the air.

So there's the challenge - 1) More stability in the kernel's development. 2) Redhat/Canonical/Novell dedicate some resources to driver development offering non-disclosure agreements to manufacturers and 3) Listen to what people actually want.

I mean seriously - tape drivers? Is this 1999?

---

### Post by khurrum1990 on 2007-11-04
You r right it some ways, but think about this Nvdia and ATI for example are manufacturing drivers for Linux so when I get an Nvidia card, it should function completely so that I get what I paid for. I paid for their product and now they should make drivers that work, this is their duty. They do it for Windows so they should do this for us as well.

Also like I suggested before kernel developers should develop a new power management system in Linux something that works no matter what. I don't think its such a big task for them.

---

### Post by ddrichardson on 2007-11-04
A *new* APM system? Its not that simple, that's a hardware function not a software one. The one area I think could be improved is in how the system actually uses power, an area I know my industry is interested in.

You are right of course that ATI and nVidia are developing drivers but graphics cards are a relatively expensive hardware addition of which more development costs can be absorbed. The problem with most new users is the cheaper hardware such as card readers and webcams which are in a very competitive market where costs are kept low and these companies are much less likely to see any benefit in developing for Linux - especially given the number of distributions out there. This is the sort of thing that would really benefit from community development.

---

### Post by khurrum1990 on 2007-11-05
Yeah u have a good point that small hardware manufacturer's for webcams and stuff won't benefit in making drivers for us, but I think we can handle small stuff on our owns. Linux developers need to make deals with bigger companies to provide fully functional drivers. I can't believe no company sees advantages in making good drivers for us. If Nvidia makes a fully functional driver then I bet every Linux user will turn to it, our market is small but its not that small.

What do u think?

---

### Post by ddrichardson on 2007-11-05
I don't know if enough people are yet prepared to vote with their wallets yet. I mean there are people like me that avoid hardware that isn't Linux friendly but many people view Ubuntu, given its current marketing, as a drop in replacement. If it doesn't work well with ATI cards then they are likely to go back to Windows rather than buy a new card.

Things are changing though. Now AMD owns ATI and are starting to release specs we should start seeing progress here.

Its chicken and egg though - until Linux gains much more desktop acceptance many companies will see no need to invest, unfortunately until there are drivers, many users will see no need to switch.

---

### Post by khurrum1990 on 2007-11-05
Yeah u r right, but can u answer me this for example when a company does make drivers for Linux why don't they make complete drivers for example in this case Nvidia, they r making drivers, but why not make sure suspend to ram and disk work as well? Thanks!

---

### Post by ddrichardson on 2007-11-05
> **khurrum1990 said:**
> Yeah u r right, but can u answer me this for example when a company does make drivers for Linux why don't they make complete drivers for example in this case Nvidia, they r making drivers, but why not make sure suspend to ram and disk work as well? Thanks!nVidia are not responsible for APM implementation, the closest they come is nForce chipsets - APM is a BIOS function and therefore down to Phoenix et al to consolidate with the hardware manufacturer.

Basically what it boils down to is that older machines use APM which is BIOS based, ACPI on the other hand is more than this as it not only provides power management but a common interface for recognising and configuring devices. The thing is though that despite it being an open standard, its not actually that compatible outside the core companies who worked on it.

I also know that none of this makes a jot of difference to someone, such as yourself, who is having problems with suspend.

---

### Post by khurrum1990 on 2007-11-05
Thanks for the information, but I found out what the problem was. The latest Ubuntu 7.10 kernel 2.6.22-14 broke suspend and hibernate for me and there was a bug report, so far the only solution is to downgrade to kernel 2.6.22-12. Now everything seems to work though. Just one question using a previous 7.10 kernel won't cause any problems would it in the future cause so far everything works great. Thanks again.

---

### Post by ddrichardson on 2007-11-05
It shouldn't do but that's why grub keeps a link for the previous kernel.

---

### Post by khurrum1990 on 2007-11-05
Thanks for the help!

---

