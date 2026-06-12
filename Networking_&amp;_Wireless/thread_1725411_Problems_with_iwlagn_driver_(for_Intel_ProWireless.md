---
title: "Problems with iwlagn driver (for Intel Pro/Wireless 4965 AGN)"
date: 2011-04-09
forum: Networking &amp; Wireless
---

### Post by JSulli on 2011-04-09
Hi
Although the wireless actually works with the distro itself, I am having problems making my wireless work with a much-cleaned-up kernel .config I am using (distro based kernels of course take ages to compile because of all the redundant drivers etc. that end up being built).

This is my new development machine and I need it to build and test mainline kernels - I am having trouble with what, subject to a lot of hunting round, I think is a distro-specific (not kernel-specific) determination which I cannot find.

I am using Kubuntu (according to lsb_release -a Ubuntu 10.10) on a Dell XPS/M1730 laptop and the wireless is provided by:

0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

which I believe uses the iwlagn driver.  On the distro kernel, lspci -v:

    0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
            Subsystem: Intel Corporation Device 1121
            Flags: bus master, fast devsel, latency 0, IRQ 41
            Memory at f0efe000 (64-bit, non-prefetchable) [size=8K]
            Capabilities: <access denied>
            Kernel driver in use: iwlagn
            Kernel modules: iwlagn

As I have tested it:
The wireless works fine with the native distro kernel.
The wireless works fine with mainline kernels I build using the distro .config.
The wireless is not working with mainline kernels using my .config, and I think the problem is that it's not finding the microcode that iwlagn needs. From dmesg:

    4.070914] iwlagn 0000:0c:00.0: request for firmware file 'iwlwifi-4965-2.ucode' failed.
[    4.071135] iwlagn 0000:0c:00.0: no suitable firmware found!

From the kernel config help (make menuconfig):

    CONFIG_IWLAGN:                                                                    &#9474;
      &#9474;                                                                                          &#9474;
      &#9474; Select to build the driver supporting the:                               &#9474;
      &#9474;                                                                                          &#9474;
      &#9474; Intel Wireless WiFi Link Next-Gen AGN                                  &#9474;
      &#9474;                                                                                          &#9474;
      &#9474; This driver uses the kernel's mac80211 subsystem.                &#9474;
      &#9474;                                                                                          &#9474;
      &#9474; In order to use this driver, you will need a microcode (uCode)  &#9474;
      &#9474; image for it. You can obtain the microcode from:                    &#9474;
      &#9474;                                                                                          &#9474;
      &#9474;         <http://intellinuxwireless.org/>.                                    &#9474;
      &#9474;                                                                                          &#9474;
      &#9474; The microcode is typically installed in /lib/firmware. You can    &#9474;
      &#9474; look in the hotplug script /etc/hotplug/firmware.agent to           &#9474;
      &#9474; determine which directory FIRMWARE_DIR is set to when the script    &#9474;
      &#9474; runs.                                                                                    &#9474;
      &#9474;  ...<snip>....

Looking on Intel's website reveals the microcode is  iwlwifi-4965-2.ucode.

Checking in  /lib/firmware/ reveals the microcode is indeed present:

    julie@julie-MXG071:~$ ls /lib/firmware/iwlwifi-4965*
    /lib/firmware/iwlwifi-4965-2.ucode

However, looking at the next sentence from the CONFIG_IWLAGN help:

    You can look in the hotplug script /etc/hotplug/firmware.agent
    to determine which directory FIRMWARE_DIR is set to when the
    script runs.

there is no file named firmware.agent on my system (nor indeed an /etc/hotplug/ directory) so clearly kubuntu isn't using this for the microcode.
Can anyone tell me what it _is_ using so I can successfully set it up for my custom config? Or am I on completely the wrong track here?  :-)

Cheers
Julie

---

