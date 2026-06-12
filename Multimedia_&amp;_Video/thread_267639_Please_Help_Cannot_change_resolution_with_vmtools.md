---
title: "Please Help: Cannot change resolution with vmtools"
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by sgulics on 2006-09-28
Hello all, 

I am in dire need of help. This problem is driving me crazy and it seems I cannot find any solutions on line. 

I just installed Unbuntu on VMWare running on a WIndowXP machine. Install went great. I then installed VMwareTools-5.5.1-19175 using the instruction provided here:
[http://www.abbeyworkshop.com/2006/06/04/ubuntu-vmware-install.html](http://www.abbeyworkshop.com/2006/06/04/ubuntu-vmware-install.html)

That also went ok but I did not notice the following:
No X install found.

I did not think that mattered. I went to change the resolution and it is still stuck at 1024x768. The tools look like they were installed property. The tool box is installed in usr/bin/. 

After looking around online I noticed people talking about a prompt that asks you to chose the resolution when you run vmware-config-tools.pl. I never go that option. 

Below is a little bit of the output from running the config. 

Thanks, 
Steve

make: Entering directory `/tmp/vmware-config0/vmxnet-only'
make -C /lib/modules/2.6.15-27-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
  CC [M]  /tmp/vmware-config0/vmxnet-only/vmxnet.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config0/vmxnet-only/vmxnet.mod.o
  LD [M]  /tmp/vmware-config0/vmxnet-only/vmxnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
cp -f vmxnet.ko ./../vmxnet.o
make: Leaving directory `/tmp/vmware-config0/vmxnet-only'
The module loads perfectly in the running kernel.

**No X install found.**

Starting VMware Tools services in the virtual machine:
   Switching to guest configuration:                                   done
   Guest filesystem driver:                                            done
   DMA setup:                                                          done
   Guest operating system daemon:                                      done

The configuration of VMware Tools 5.5.1 build-19175 for Linux for this running
kernel completed successfully.

You must restart your X session before any mouse or graphics changes take
effect.

You can now run VMware Tools by invoking the following command:
"/usr/bin/vmware-toolbox" during an XFree86 session.

To use the vmxnet driver, restart networking using the following commands:
/etc/init.d/networking stop
rmmod pcnet32
rmmod vmxnet
depmod -a
modprobe vmxnet
/etc/init.d/networking start

Enjoy,

--the VMware team

---

