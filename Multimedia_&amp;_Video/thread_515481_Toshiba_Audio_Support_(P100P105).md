---
title: "Toshiba Audio Support (P100/P105)"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by JamesTheBard on 2007-08-02
After searching around for around four days on how to configure alsa to allow my sound card to work.  This involved changing my /etc/modprobe.d/alsa-base with every option that was listed on the various webpages and wiki's located around the internet.

After that, I searched a bit more and found a guide written for SLED 10 that creates a custom DSDT file (for more information about ACPI , read **[here]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface")**.

Before I start, 90% of the credit (which is to say that all of it save me kludging around on how to do **[this]("http://www.linuxquestions.org/questions/showthread.php?t=531575")** in Ubuntu) goes to LuisC-SM.  Also some thanks goes to the Gentoo forums.

Currently, I know that this works on v2.40 and v3.30 BIOSes.

Here is my current setup (WRT audio)

```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03) (prog-if 00 [VGA])
	Subsystem: Toshiba America Info Systems Unknown device [1179:ff31]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

```

So far, I can only attest to this working on both BIOS versions on my laptop so YMMV.

First, lets get our tools installed.
```
 $ sudo apt-get install iasl
```
Then, lets grab a copy of the computer's DSDT file by executing:
```
 $ sudo cat /proc/acpi/dsdt > dsdt.dat
```
To make this something we can actually edit, we will use the Intel DSL Compiler to decompile the .dat file and save it as dsdt.dsl.
```
 $ iasl -d dsdt.dat 
```
Now, we're going to open the newly created file in GEdit.  You can either open it up via the GUI or run it like this:
```
 $ gedit dsdt.dsl
```
This is the complex step so be careful!  First, replace all occurances of *PNP0C14 with PNP0C14.  Then search for the term "Linux".  You will end up commenting out the entire If statement after "Store (0x07D0, OSYS)" until you get to the third closing "}".  Right before the fourth, you will add "Store (0x07D6, OSYS) // Fake Windows 2006".  The result should look almost exactly like the following snippet.
```
    Scope (\_SB)
    {
        Method (_INI, 0, NotSerialized)
        {
            If (DTSE)
            {
                TRAP (0x47)
            }

            Store (0x07D0, OSYS)
//            If (CondRefOf (_OSI, Local0))
//            {
//                If (_OSI ("Linux"))
//                {
//                    Store (0x03E8, OSYS)
//                }
//                Else
//                {
//                    Store (0x07D1, OSYS)
//                    If (_OSI ("Windows 2001 SP2"))
//                    {
//                        Store (0x07D2, OSYS)
//                    }

//                    If (_OSI ("Windows 2001.1"))
//                    {
//                        Store (0x07D3, OSYS)
//                    }

//                    If (_OSI ("Windows 2001.1 SP1"))
//                    {
//                        Store (0x07D4, OSYS)
//                    }

//                    If (_OSI ("Windows 2006"))
//                    {
//                        Store (0x07D6, OSYS)
//                    }

//                    If (LAnd (MPEN, LEqual (OSYS, 0x07D1)))
//                    {
//                        TRAP (0x3D)
//                    }
//                }
//            }
	Store (0x07D6, OSYS) // Fake Windows 2006
        }
```
Now that this is done, save the file and exit GEdit.  Time to go back to the CLI.  Recompile the newly created dsdt.dsl file.
```
 $ iasl -tc -f dsdt.dsl
```
This will give you a new file named "dsdt.aml" in your home folder (assuming you started there in the beginning).
The next step is to move this newly created file to the /etc/initramfs-tools folder, then add the file to the initrd that Ubuntu uses to boot with so that it will load when the computer boots.
```
 $ sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
 $ sudo dpkg-reconfigure linux-image-$(uname -r)
```
The final step: simply reboot.

**Acknowledgeemnts**
[LIST]
[*]To Luis C. Suárez for writing this guide up for SLED 10.
[*]To the Gentoo guys for writing up that it worked for something other than v2.40 BIOS
[*]Anyone that I've forgotten to mention due to lack of sleep.
[/LIST]

NOTES: When decompiling and recompiling using "iasl" you will see error messages.  These are to be expected.  Also, I had already updated my alsa drivers to 1.0.14 using the following command as root.```
 # hg clone http://hg.alsa-project.org/alsa-kernel alsa-kernel && hg clone http://hg.alsa-project.org/alsa-driver alsa-driver && cd alsa-driver && ./hgcompile --with-cards=hda-intel --with-oss=yes --with-sequencer=yes --with-kernel=/lib/modules/$(uname -r)/build --with-debug=full && make && sudo make install-modules
```

---

### Post by mbaker1965 on 2007-10-13
Is there a fix for a newbie? This is was too complicated for somone like me who doesn't understand what the commands do.

Thanks

Mel

---

