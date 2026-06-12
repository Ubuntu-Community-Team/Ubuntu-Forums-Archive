---
title: "VMWare Server"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by gruffbaby on 2007-11-18
Hi,

I have a problem trying to start a VM (Windows 2003 server) in VMWare Server. I get an error: 

Unable to change virtual machine power state: The process exited with an error:
End of error message.

The log consists of this:

ov 18 11:58:31: vmx| Log for VMware Server pid=6915 version=1.0.3 build=build-44356 option=Release
Nov 18 11:58:31: vmx| Command line: "/usr/lib/vmware-server/bin/vmware-vmx" "-C" "-@" """" "/var/lib/vmware-server/Virtual Machines/Windows Server 2003 Enterprise Edition/Windows Server 2003 Enterprise Edition.vmx"
Nov 18 11:58:31: vmx| vmxvmdb: Index name being generated from config file
Nov 18 11:58:31: vmx| VMXVmdbConnectServerd - Trying to discover serverd
Nov 18 11:58:31: vmx| MStat: Creating Stat system.cpuusage
Nov 18 11:58:31: vmx| MStat: Creating Stat system.ram
Nov 18 11:58:31: vmx| MStat: Creating Stat system.uptime
Nov 18 11:58:31: vmx| MStat: Creating Stat system.load
Nov 18 11:58:31: vmx| Msg_Post: Error
Nov 18 11:58:31: vmx| [msg.vmmonPosix.openFailed] Could not open /dev/vmmon: No such file or directory.
Nov 18 11:58:31: vmx| Please make sure that the kernel module `vmmon' is loaded.
Nov 18 11:58:31: vmx| ----------------------------------------
Nov 18 11:58:31: vmx| POST(no connection): Could not open /dev/vmmon: No such file or directory.
Nov 18 11:58:31: vmx| Please make sure that the kernel module `vmmon' is loaded.
Nov 18 11:58:31: vmx| 
Nov 18 11:58:31: vmx| Msg_Post: Error
Nov 18 11:58:31: vmx| [msg.vmmonPosix.initFailed] Failed to initialize monitor device.
Nov 18 11:58:31: vmx| ----------------------------------------
Nov 18 11:58:31: vmx| POST(no connection): Failed to initialize monitor device.
Nov 18 11:58:31: vmx| 
Nov 18 11:58:31: vmx| Module VMMon initialization failed.
Nov 18 11:58:31: vmx| Flushing VMX VMDB connections
Nov 18 11:58:31: vmx| Failed to initialize VM

Any ideas? I do not want to re-install the VM again. I am using kernel 2.6.22-14.

Thanks.

---

### Post by sethvath on 2007-11-18
This is an issue with the kernel. Read the following link and apply the patch

[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1623](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1623)

In terminal: sudo ./runme.pl

You should be able to compile vmmon then

---

### Post by gruffbaby on 2007-11-18
Thanks for the reply.

Unfortunately when I run the script I get the followin:

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] y

sh: /usr/bin/vmware-config.pl: not found

---

