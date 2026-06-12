---
title: "Wi Fi not found on satellite L300 in intrepid"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by real_magiz on 2009-02-13
Wi Fi not found Toshiba satellite L300

my lsusb shows

BUs 007 Device 003: ID 0bda:8198 Realtek Semiconductor Corp.

and

 dmesg |grep rtl8198 shows nothing.

what should I do??
 nhasian said on 2009-02-10:

actually the command that would help us out would be:

lshw -C network

to try to get your wifi working go to System &#8594; Administration &#8594; Software Sources click on the Updates tab, then check the box for Unsupported updates (intrepid-backports). after you've enabled the backports update your ubuntu software from a terminal with the commands:

sudo apt-get update
sudo apt-get upgrade

you may need to reboot. after that go to System &#8594; Administration &#8594; Hardware Drivers and enable any restricted drivers you have available.
 Mark Rijckenberg said on 2009-02-10:

Hi,

If nhasian's procedure does not work, then please try the solution from forumuser joecefiro at the following location:

[http://ubuntuforums.org/showthread.php?t=900791&page=4](http://ubuntuforums.org/showthread.php?t=900791&page=4)

Please make sure you are using Ubuntu 8.10 and NOT Ubuntu 8.04.

Regards,

Mark
 real_magiz said on 2009-02-10:

mine is RTL8198. not 8187.

On Tue, Feb 10, 2009 at 2:56 PM, Mark Rijckenberg <
[email]question60501@answers.launchpad.net[/email]> wrote:

[...]
> Your question #60501 on Ubuntu changed:
> [https://answers.launchpad.net/ubuntu/+question/60501](https://answers.launchpad.net/ubuntu/+question/60501)
>
> Mark Rijckenberg proposed the following answer:
> Hi,
>
> If nhasian's procedure does not work, then please try the solution from
> forumuser joecefiro at the following location:
>
> [http://ubuntuforums.org/showthread.php?t=900791&page=4](http://ubuntuforums.org/showthread.php?t=900791&page=4)
>
> Please make sure you are using Ubuntu 8.10 and NOT Ubuntu 8.04.
>
> Regards,
>
> Mark
>
> --
> If this answers your question, please go to the following page to let us
> know that it is solved:
> [https://answers.launchpad.net/ubuntu/+question/60501/+confirm?answer_id=1](https://answers.launchpad.net/ubuntu/+question/60501/+confirm?answer_id=1)
>
> If you still need help, you can reply to this email or go to the
> following page to enter your feedback:
> [https://answers.launchpad.net/ubuntu/+question/60501](https://answers.launchpad.net/ubuntu/+question/60501)
>
> You received this question notification because you are a direct
> subscriber of the question.
>

[...]
--
Nay Myo
 real_magiz said on 2009-02-10:

lshw -C network shows

**-network

    description: Ethernet Interface
    Product: RTL8101E/RTL8102E PCI Express Fast Ethernet Controller
    vendor: Realtek Semiconductor Co., Ltd.

    physical id: 0
    bus info: pci@0000:02:00.0
    logical name: eth0
    version: 02
    serial : 00:ie:33:3b:4d:74
    capacity: 1GB/s
    width: 64bits
    clock: 33Mhz

*

On Tue, Feb 10, 2009 at 11:56 AM, nhasian <
[email]question60501@answers.launchpad.net[/email]> wrote:

[...]
> Your question #60501 on Ubuntu changed:
> [https://answers.edge.launchpad.net/ubuntu/+question/60501](https://answers.edge.launchpad.net/ubuntu/+question/60501)
>
> Status: Open => Answered
>
> nhasian proposed the following answer:
> actually the command that would help us out would be:
>
> lshw -C network
>
> to try to get your wifi working go to System &#8594; Administration &#8594; Software
> Sources click on the Updates tab, then check the box for Unsupported
> updates (intrepid-backports). after you've enabled the backports update
> your ubuntu software from a terminal with the commands:
>
> sudo apt-get update
> sudo apt-get upgrade
>
> you may need to reboot. after that go to System &#8594; Administration &#8594;
> Hardware Drivers and enable any restricted drivers you have available.
>
> --
> If this answers your question, please go to the following page to let us
> know that it is solved:
>
> [https://answers.edge.launchpad.net/ubuntu/+question/60501/+confirm?answer_id=0](https://answers.edge.launchpad.net/ubuntu/+question/60501/+confirm?answer_id=0)
>
> If you still need help, you can reply to this email or go to the
> following page to enter your feedback:
> [https://answers.edge.launchpad.net/ubuntu/+question/60501](https://answers.edge.launchpad.net/ubuntu/+question/60501)
>
> You received this question notification because you are a direct
> subscriber of the question.
>

[...]
--
Nay Myo
 real_magiz said on 2009-02-10:

[...]
>
> You gave more information on the question:
> lshw -C network shows
>
> lshw -C network shows
>
> **-network
>
>
> description: Ethernet Interface
> Product: RTL8101E/RTL8102E PCI Express Fast Ethernet Controller
> vendor: Realtek Semiconductor Co., Ltd.
>
> physical id: 0
> bus info: pci@0000:02:00.0
> logical name: eth0
> version: 02
> serial : 00:ie:33:3b:4d:74
> capacity: 1GB/s
> width: 64bits
> clock: 33Mhz
>
> capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet
> physical tp 10bt 10bt-fd 100bt-fd autonegotiation
> configuration: autonegotiation=on broadcast=yes driver=r8169
> driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169
> multicast=yes port=twisted pair
>
>
>
>
> *-network Disabled
>
> description: Ethernet interface
> physical id: 1
> logical name: pan0
> serial: f6:22:df:74:4e:8b
> capabilities: ethernet physical
> configuration: broadcast=yes drive=bridge driverversion=2.3
> firmware=N/A link=yes multicast=yes
>
>
>
>
>
>
> On Tue, Feb 10, 2009 at 11:56 AM, nhasian <
> [email]question60501@answers.launchpad.net[/email]> wrote:
>
> > Your question #60501 on Ubuntu changed:
> > [https://answers.edge.launchpad.net/ubuntu/+question/60501](https://answers.edge.launchpad.net/ubuntu/+question/60501)
> >
> > Status: Open => Answered
> >
> > nhasian proposed the following answer:
> > actually the command that would help us out would be:
> >
> > lshw -C network
> >
> > to try to get your wifi working go to System &#8594; Administration &#8594; Software
> > Sources click on the Updates tab, then check the box for Unsupported
> > updates (intrepid-backports). after you've enabled the backports update
> > your ubuntu software from a terminal with the commands:
> >
> > sudo apt-get update
> > sudo apt-get upgrade
> >
> > you may need to reboot. after that go to System &#8594; Administration &#8594;
> > Hardware Drivers and enable any restricted drivers you have available.
> >
> > --
> > If this answers your question, please go to the following page to let us
> > know that it is solved:
> >
> >
> [https://answers.edge.launchpad.net/ubuntu/+question/60501/+confirm?answer_id=0](https://answers.edge.launchpad.net/ubuntu/+question/60501/+confirm?answer_id=0)
> >
> > If you still need help, you can reply to this email or go to the
> > following page to enter your feedback:
> > [https://answers.edge.launchpad.net/ubuntu/+question/60501](https://answers.edge.launchpad.net/ubuntu/+question/60501)
> >
> > You received this question notification because you are a direct
> > subscriber of the question.
> >
>
>
> --
> Nay Myo
>
> You received this question notification because you are a direct
> subscriber of the question.
>

[...]
--
Nay Myo
 Mark Rijckenberg said on 2009-02-10:

Hi,

Try testing your wireless card using the Ubuntu 9.04 alpha 4 LiveCD, which you can download here:

[http://cdimage.ubuntu.com/releases/jaunty/alpha-4/jaunty-desktop-i386.iso](http://cdimage.ubuntu.com/releases/jaunty/alpha-4/jaunty-desktop-i386.iso)

If wireless does not work during the Ubuntu 9.04 Alpha 4 LiveCD session, please connect your network card to the wireless router using a LAN cable.

Then please follow this procedure:

Step 1: Open Terminal from "Applications->Accessories->Terminal"

Step 2: Run the following commands (copy-paste each line below to the Terminal then hit <enter> after each line)

sudo iwlist scanning
nm-tool
iwconfig
ifconfig
sudo lshw -C network
lspci -nn
lsusb
uname -a
dmesg | grep ound
dmesg | grep illswitch

Step 3: Post results (cut/paste terminal output from each command) here

Regards,

Mark
 real_magiz said on 2009-02-11:

is your live CD mean Ubuntu version 4 or 5??

I think i have version 5. but i m not sure.

I have now installed Intrepid version 8.10.

even If it can work under live Jaunty CD, it is nothing for me, coz i wont
install that old version.

Could you please let me know the point of using live CD.??

the other thing is to connect to my wireless router with LAN cable.

 is it just to see output??

coz i will use with any Wireless Router . not only to use with the same
router ever.

On Tue, Feb 10, 2009 at 7:01 PM, Mark Rijckenberg <
[email]question60501@answers.launchpad.net[/email]> wrote:

[...]
> Your question #60501 on Ubuntu changed:
> [https://answers.launchpad.net/ubuntu/+question/60501](https://answers.launchpad.net/ubuntu/+question/60501)
>
> Status: Open => Answered
>
> Mark Rijckenberg proposed the following answer:
> Hi,
>
> Try testing your wireless card using the Ubuntu 9.04 alpha 4 LiveCD,
> which you can download here:
>
> [http://cdimage.ubuntu.com/releases/jaunty/alpha-4/jaunty-](http://cdimage.ubuntu.com/releases/jaunty/alpha-4/jaunty-)
> desktop-i386.iso<http://cdimage.ubuntu.com/releases/jaunty/alpha-4/jaunty-%0Adesktop-i386.iso>
>
> If wireless does not work during the Ubuntu 9.04 Alpha 4 LiveCD session,
> please connect your network card to the wireless router using a LAN
> cable.
>
> Then please follow this procedure:
>
> Step 1: Open Terminal from "Applications->Accessories->Terminal"
>
> Step 2: Run the following commands (copy-paste each line below to the
> Terminal then hit <enter> after each line)
>
> sudo iwlist scanning
> nm-tool
> iwconfig
> ifconfig
> sudo lshw -C network
> lspci -nn
> lsusb
> uname -a
> dmesg | grep ound
> dmesg | grep illswitch
>
> Step 3: Post results (cut/paste terminal output from each command) here
>
> Regards,
>
> Mark
>
> --
> If this answers your question, please go to the following page to let us
> know that it is solved:
> [https://answers.launchpad.net/ubuntu/+question/60501/+confirm?answer_id=5](https://answers.launchpad.net/ubuntu/+question/60501/+confirm?answer_id=5)
>
> If you still need help, you can reply to this email or go to the
> following page to enter your feedback:
> [https://answers.launchpad.net/ubuntu/+question/60501](https://answers.launchpad.net/ubuntu/+question/60501)
>
> You received this question notification because you are a direct
> subscriber of the question.
>

[...]
--
Nay Myo
 Mark Rijckenberg said on 2009-02-11:

Hi,

I am talking about Ubuntu 9.04 alpha 4 LiveCD (alpha version, will be released in April 2009)

Jaunty Jackalope is not an old version of Ubuntu, but the newest version (newer than Ubuntu 8.10)

The point of using the LiveCD is to see if the newest version of Ubuntu works better with your wireless card. And if it does not, then you will not waste time installing Ubuntu 9.04 to your harddisk.

Connecting your LAN cable to the router and your network card is necessary so that you can send the output of the commands above to us using Ubuntu 9.04.

Regards,

Mark
 real_magiz said 5 hours ago:

brother,

I downloaded jaunty and boot with that.

but i can't really use my touch pad. so i can't open my terminal. coz i dont know keyboard shortcuts.

I am wondering why my touchpad is not working in LIVE CD.

thanks

---

