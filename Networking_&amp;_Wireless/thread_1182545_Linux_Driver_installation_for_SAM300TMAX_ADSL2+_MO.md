---
title: "Linux Driver installation for SAM300TMAX ADSL2+ MODEM"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by rakeshkumarguptaias on 2009-06-09
Hello, 
  
I have switched from Windows to Ubuntu Linux (9.04 version) recently and have been very pleased with the experience so far.  
  
However, after changing my ADSL MODEM a few days back, I am unable to install its driver within Ubuntu. The Modem is SAM300TMax ADSL2+. It has come with a CD containing both the Windows as well as Linux drivers. I am connecting the modem through the USB port since there is no ethernet network card installed on my desktop. The driver in Windows XP has been installed easily and is working fine after connecting it through the USB port. 
  
However, the Linux driver available in the CD could not be compiled or installed. The modem is also not being detected automatically when connected through the USB port in UBUNTU. 
  
The readme file in the Linux Driver on Cd gives the following instructions: 
 
 
[I]3. Installation 
 
3.1 Installation from source code 
 
Note: Do not plug and power on CPE before installing the driver; 
 
All operations in this section needs root's privilege. 
 
tar zxvf trendchip-1.2.tar.gz 
 
cd trendchip-1.2 
 
make 
 
make install  
[/I] 
 
 
When I followed these instructions and extracted the files using tar and then after going to trendchip-1.2 directory and then issued the make command (sudo make), the source could not be compiled. it gives error 1. The detailed printout of the system on issuing the command is as follows:

Hello, 
 
 
 
I have switched from Windows to Ubuntu Linux (9.04 version) recently and have been very pleased with the experience so far.  
 
 
 
However, after changing my ADSL MODEM a few days back, I am unable to install its driver within Ubuntu. The Modem is SAM300TMax ADSL2+. It has come with a CD containing both the Windows as well as Linux drivers. I am connecting the modem through the USB port since there is no ethernet network card installed on my desktop. The driver in Windows XP has been installed easily and is working fine after connecting it through the USB port. 
 
 
 
However, the Linux driver available in the CD could not be compiled or installed. The modem is also not being detected automatically when connected through the USB port in UBUNTU. 
 
 
 
The readme file in the Linux Driver on Cd gives the following instructions: 
 
 
 
3. Installation 
 
3.1 Installation from source code 
 
Note: Do not plug and power on CPE before installing the driver; 
 
All operations in this section needs root's privilege. 
 
tar zxvf trendchip-1.2.tar.gz 
 
cd trendchip-1.2 
 
make 
 
make install  
 
 When I followed these instructions and extracted the files using tar and then after going to trendchip-1.2 directory and then issued the make command (sudo make), the source could not be compiled. it gives error 1. The detailed printout of the system on issuing the command is as follows:

[I]sudo make
[sudo] password for rakesh: 
gcc -Wall -D__KERNEL__ -DMODULE -I/usr/src/linux-2.6.28-11-generic/include -O -g -I..   -c -o trendchip.o trendchip.c
trendchip.c:19:24: error: linux/slab.h: No such file or directory
trendchip.c:20:24: error: linux/init.h: No such file or directory
trendchip.c:21:25: error: linux/delay.h: No such file or directory
In file included from /usr/include/linux/socket.h:23,
                 from /usr/include/linux/if.h:23,
                 from /usr/include/linux/netdevice.h:28,
                 from trendchip.c:22:
/usr/include/linux/uio.h:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘iov_length’
/usr/include/linux/uio.h:47: error: expected declaration specifiers or ‘...’ before ‘size_t’
trendchip.c:23:31: error: linux/etherdevice.h: No such file or directory
trendchip.c:24:26: error: linux/module.h: No such file or directory
trendchip.c:26:25: error: asm/uaccess.h: No such file or directory
trendchip.c:29:23: error: linux/usb.h: No such file or directory
In file included from trendchip.c:31:
trendchip.h:78: error: field ‘ctrl_dr’ has incomplete type
trendchip.h:79: error: field ‘rx_urb’ has incomplete type
trendchip.h:79: error: field ‘tx_urb’ has incomplete type
trendchip.h:79: error: field ‘intr_urb’ has incomplete type
trendchip.h:79: error: field ‘ctrl_urb’ has incomplete type
trendchip.h:80: error: requested alignment is not a constant
trendchip.h:81: error: requested alignment is not a constant
trendchip.h:82: error: requested alignment is not a constant
trendchip.c:43: error: array type has incomplete element type
trendchip.c:45: warning: implicit declaration of function ‘USB_DEVICE’
trendchip.c: In function ‘read_bulk_callback’:
trendchip.c:64: error: dereferencing pointer to incomplete type
trendchip.c:66: error: dereferencing pointer to incomplete type
trendchip.c:70: error: dereferencing pointer to incomplete type
trendchip.c:71: error: ‘USB_ST_NOERROR’ undeclared (first use in this function)
trendchip.c:71: error: (Each undeclared identifier is reported only once
trendchip.c:71: error: for each function it appears in.)
trendchip.c:73: error: ‘USB_ST_URB_KILLED’ undeclared (first use in this function)
trendchip.c:76: warning: implicit declaration of function ‘dbg’
trendchip.c:76: error: dereferencing pointer to incomplete type
trendchip.c:86: warning: implicit declaration of function ‘netif_device_present’
trendchip.c:101: error: dereferencing pointer to incomplete type
trendchip.c:104: error: ‘USB_ST_NORESPONSE’ undeclared (first use in this function)
trendchip.c:109: error: dereferencing pointer to incomplete type
trendchip.c:109: error: dereferencing pointer to incomplete type
trendchip.c:129: warning: implicit declaration of function ‘dev_alloc_skb’
trendchip.c:129: warning: assignment makes pointer from integer without a cast
trendchip.c:135: error: dereferencing pointer to incomplete type
trendchip.c:139: warning: implicit declaration of function ‘eth_copy_and_sum’
trendchip.c:143: warning: implicit declaration of function ‘skb_put’
trendchip.c:145: error: dereferencing pointer to incomplete type
trendchip.c:145: warning: implicit declaration of function ‘eth_type_trans’
trendchip.c:148: warning: implicit declaration of function ‘netif_rx’
trendchip.c:157: warning: implicit declaration of function ‘FILL_BULK_URB’
trendchip.c:158: warning: implicit declaration of function ‘usb_rcvbulkpipe’
trendchip.c:164: warning: implicit declaration of function ‘usb_submit_urb’
trendchip.c:165: warning: implicit declaration of function ‘warn’
trendchip.c: In function ‘write_bulk_callback’:
trendchip.c:174: error: dereferencing pointer to incomplete type
trendchip.c:179: warning: implicit declaration of function ‘err’
trendchip.c:191: error: dereferencing pointer to incomplete type
trendchip.c:192: error: dereferencing pointer to incomplete type
trendchip.c:192: error: dereferencing pointer to incomplete type
trendchip.c:197: error: dereferencing pointer to incomplete type
trendchip.c:197: error: ‘jiffies’ undeclared (first use in this function)
trendchip.c:198: warning: implicit declaration of function ‘netif_wake_queue’
trendchip.c: In function ‘intr_callback’:
trendchip.c:224: error: dereferencing pointer to incomplete type
trendchip.c:231: error: dereferencing pointer to incomplete type
trendchip.c:232: error: ‘USB_ST_NOERROR’ undeclared (first use in this function)
trendchip.c:234: error: ‘USB_ST_URB_KILLED’ undeclared (first use in this function)
trendchip.c:237: error: dereferencing pointer to incomplete type
trendchip.c:240: error: dereferencing pointer to incomplete type
trendchip.c:252: warning: implicit declaration of function ‘netif_carrier_off’
trendchip.c: In function ‘enable_net_traffic’:
trendchip.c:267: warning: implicit declaration of function ‘usb_set_interface’
trendchip.c: In function ‘CDCEther_tx_timeout’:
trendchip.c:301: error: dereferencing pointer to incomplete type
trendchip.c:310: error: dereferencing pointer to incomplete type
trendchip.c:313: error: ‘USB_ASYNC_UNLINK’ undeclared (first use in this function)
trendchip.c:314: warning: implicit declaration of function ‘usb_unlink_urb’
trendchip.c: At top level:
trendchip.c:320: warning: ‘struct sk_buff’ declared inside parameter list
trendchip.c:320: warning: its scope is only this definition or declaration, which is probably not what you want
trendchip.c: In function ‘CDCEther_start_xmit’:
trendchip.c:322: error: dereferencing pointer to incomplete type
trendchip.c:330: error: dereferencing pointer to incomplete type
trendchip.c:333: error: dereferencing pointer to incomplete type
trendchip.c:336: error: dereferencing pointer to incomplete type
trendchip.c:341: warning: implicit declaration of function ‘netif_stop_queue’
trendchip.c:344: warning: implicit declaration of function ‘memcpy’
trendchip.c:344: warning: incompatible implicit declaration of built-in function ‘memcpy’
trendchip.c:344: error: dereferencing pointer to incomplete type
trendchip.c:344: error: dereferencing pointer to incomplete type
trendchip.c:348: warning: implicit declaration of function ‘usb_sndbulkpipe’
trendchip.c:363: warning: implicit declaration of function ‘netif_start_queue’
trendchip.c:368: error: dereferencing pointer to incomplete type
trendchip.c:370: error: dereferencing pointer to incomplete type
trendchip.c:370: error: ‘jiffies’ undeclared (first use in this function)
trendchip.c:374: warning: implicit declaration of function ‘dev_kfree_skb’
trendchip.c: In function ‘CDCEther_netdev_stats’:
trendchip.c:386: error: dereferencing pointer to incomplete type
trendchip.c: In function ‘CDCEther_open’:
trendchip.c:391: error: dereferencing pointer to incomplete type
trendchip.c:398: error: ‘EIO’ undeclared (first use in this function)
trendchip.c:415: warning: implicit declaration of function ‘FILL_INT_URB’
trendchip.c:417: warning: implicit declaration of function ‘usb_rcvintpipe’
trendchip.c: In function ‘CDCEther_close’:
trendchip.c:440: error: dereferencing pointer to incomplete type
trendchip.c: In function ‘netdev_ethtool_ioctl’:
trendchip.c:466: error: dereferencing pointer to incomplete type
trendchip.c:467: error: ‘u32’ undeclared (first use in this function)
trendchip.c:467: error: expected ‘;’ before ‘cmd’
trendchip.c:470: warning: implicit declaration of function ‘get_user’
trendchip.c:470: error: ‘cmd’ undeclared (first use in this function)
trendchip.c:470: error: expected expression before ‘)’ token
trendchip.c:471: error: ‘EFAULT’ undeclared (first use in this function)
trendchip.c:477: warning: implicit declaration of function ‘strncpy’
trendchip.c:477: warning: incompatible implicit declaration of built-in function ‘strncpy’
trendchip.c:479: warning: implicit declaration of function ‘sprintf’
trendchip.c:479: warning: incompatible implicit declaration of built-in function ‘sprintf’
trendchip.c:479: error: dereferencing pointer to incomplete type
trendchip.c:479: error: dereferencing pointer to incomplete type
trendchip.c:483: warning: implicit declaration of function ‘copy_to_user’
trendchip.c:490: warning: implicit declaration of function ‘netif_carrier_ok’
trendchip.c:497: error: ‘EOPNOTSUPP’ undeclared (first use in this function)
trendchip.c: In function ‘CDCEther_ioctl’:
trendchip.c:507: error: ‘ENOTTY’ undeclared (first use in this function)
trendchip.c: In function ‘parse_ethernet_class_information’:
trendchip.c:750: warning: implicit declaration of function ‘printk’
trendchip.c: In function ‘find_and_parse_ethernet_class_information’:
trendchip.c:784: error: dereferencing pointer to incomplete type
trendchip.c:785: error: dereferencing pointer to incomplete type
trendchip.c:786: error: dereferencing pointer to incomplete type
trendchip.c:794: error: dereferencing pointer to incomplete type
trendchip.c:796: error: dereferencing pointer to incomplete type
trendchip.c:796: error: dereferencing pointer to incomplete type
trendchip.c:797: error: dereferencing pointer to incomplete type
trendchip.c:802: error: dereferencing pointer to incomplete type
trendchip.c:802: error: dereferencing pointer to incomplete type
trendchip.c: In function ‘get_data_interface_endpoints’:
trendchip.c:824: error: dereferencing pointer to incomplete type
trendchip.c:825: error: dereferencing pointer to incomplete type
trendchip.c:826: error: dereferencing pointer to incomplete type
trendchip.c:833: error: dereferencing pointer to incomplete type
trendchip.c:833: error: ‘USB_ENDPOINT_XFER_BULK’ undeclared (first use in this function)
trendchip.c:836: error: dereferencing pointer to incomplete type
trendchip.c:841: error: dereferencing pointer to incomplete type
trendchip.c:841: error: ‘USB_DIR_IN’ undeclared (first use in this function)
trendchip.c:842: error: dereferencing pointer to incomplete type
trendchip.c:844: error: dereferencing pointer to incomplete type
trendchip.c:845: error: dereferencing pointer to incomplete type
trendchip.c:849: error: dereferencing pointer to incomplete type
trendchip.c:850: error: dereferencing pointer to incomplete type
trendchip.c:852: error: dereferencing pointer to incomplete type
trendchip.c:853: error: dereferencing pointer to incomplete type
trendchip.c: In function ‘verify_ethernet_data_interface’:
trendchip.c:878: error: dereferencing pointer to incomplete type
trendchip.c:879: error: dereferencing pointer to incomplete type
trendchip.c:889: error: dereferencing pointer to incomplete type
trendchip.c:890: error: dereferencing pointer to incomplete type
trendchip.c:893: error: dereferencing pointer to incomplete type
trendchip.c:894: error: dereferencing pointer to incomplete type
trendchip.c:895: error: dereferencing pointer to incomplete type
trendchip.c:896: error: dereferencing pointer to incomplete type
trendchip.c:903: error: dereferencing pointer to incomplete type
trendchip.c:905: error: dereferencing pointer to incomplete type
trendchip.c:911: error: dereferencing pointer to incomplete type
trendchip.c:916: error: dereferencing pointer to incomplete type
trendchip.c:918: error: dereferencing pointer to incomplete type
trendchip.c: In function ‘find_ethernet_comm_interface’:
trendchip.c:939: error: dereferencing pointer to incomplete type
trendchip.c:945: error: dereferencing pointer to incomplete type
trendchip.c:946: error: dereferencing pointer to incomplete type
trendchip.c:949: error: dereferencing pointer to incomplete type
trendchip.c:950: error: dereferencing pointer to incomplete type
trendchip.c:955: error: dereferencing pointer to incomplete type
trendchip.c:957: error: dereferencing pointer to incomplete type
trendchip.c:980: error: dereferencing pointer to incomplete type
trendchip.c:981: error: dereferencing pointer to incomplete type
trendchip.c:981: error: ‘USB_DIR_IN’ undeclared (first use in this function)
trendchip.c:982: error: dereferencing pointer to incomplete type
trendchip.c:982: error: ‘USB_ENDPOINT_XFER_INT’ undeclared (first use in this function)
trendchip.c:984: error: dereferencing pointer to incomplete type
trendchip.c:986: error: dereferencing pointer to incomplete type
trendchip.c: In function ‘find_valid_configuration’:
trendchip.c:1031: error: dereferencing pointer to incomplete type
trendchip.c:1032: error: dereferencing pointer to incomplete type
trendchip.c:1036: error: dereferencing pointer to incomplete type
trendchip.c:1045: error: dereferencing pointer to incomplete type
trendchip.c: At top level:
trendchip.c:1066: warning: ‘struct usb_config_descriptor’ declared inside parameter list
trendchip.c: In function ‘check_for_claimed_interfaces’:
trendchip.c:1073: error: dereferencing pointer to incomplete type
trendchip.c:1074: error: dereferencing pointer to incomplete type
trendchip.c:1075: warning: implicit declaration of function ‘usb_interface_claimed’
trendchip.c: In function ‘set_ethernet_addr’:
trendchip.c:1158: warning: incompatible implicit declaration of built-in function ‘memcpy’
trendchip.c:1158: error: dereferencing pointer to incomplete type
trendchip.c: In function ‘log_device_info’:
trendchip.c:1181: error: dereferencing pointer to incomplete type
trendchip.c:1184: warning: implicit declaration of function ‘usb_string’
trendchip.c:1190: error: dereferencing pointer to incomplete type
trendchip.c:1199: error: dereferencing pointer to incomplete type
trendchip.c:1208: error: dereferencing pointer to incomplete type
trendchip.c:1211: warning: implicit declaration of function ‘info’
trendchip.c:1211: error: dereferencing pointer to incomplete type
trendchip.c:1213: error: dereferencing pointer to incomplete type
trendchip.c: In function ‘CDCEther_probe’:
trendchip.c:1240: error: dereferencing pointer to incomplete type
trendchip.c:1240: error: dereferencing pointer to incomplete type
trendchip.c:1245: error: dereferencing pointer to incomplete type
trendchip.c:1256: warning: implicit declaration of function ‘kmalloc’
trendchip.c:1256: error: ‘GFP_KERNEL’ undeclared (first use in this function)
trendchip.c:1256: warning: assignment makes pointer from integer without a cast
trendchip.c:1262: warning: implicit declaration of function ‘memset’
trendchip.c:1262: warning: incompatible implicit declaration of built-in function ‘memset’
trendchip.c:1269: warning: implicit declaration of function ‘kfree’
trendchip.c:1275: warning: implicit declaration of function ‘usb_set_configuration’
trendchip.c:1315: warning: implicit declaration of function ‘init_etherdev’
trendchip.c:1315: warning: assignment makes pointer from integer without a cast
trendchip.c:1326: error: dereferencing pointer to incomplete type
trendchip.c:1327: warning: implicit declaration of function ‘SET_MODULE_OWNER’
trendchip.c:1328: error: dereferencing pointer to incomplete type
trendchip.c:1329: error: dereferencing pointer to incomplete type
trendchip.c:1330: error: dereferencing pointer to incomplete type
trendchip.c:1330: error: ‘HZ’ undeclared (first use in this function)
trendchip.c:1331: error: dereferencing pointer to incomplete type
trendchip.c:1332: error: dereferencing pointer to incomplete type
trendchip.c:1333: error: dereferencing pointer to incomplete type
trendchip.c:1334: error: dereferencing pointer to incomplete type
trendchip.c:1335: error: dereferencing pointer to incomplete type
trendchip.c:1336: error: dereferencing pointer to incomplete type
trendchip.c:1346: warning: implicit declaration of function ‘usb_control_msg’
trendchip.c:1346: warning: implicit declaration of function ‘usb_sndctrlpipe’
trendchip.c:1355: warning: implicit declaration of function ‘usb_driver_claim_interface’
trendchip.c:1356: error: dereferencing pointer to incomplete type
trendchip.c:1359: warning: implicit declaration of function ‘usb_inc_dev_use’
trendchip.c: In function ‘CDCEther_disconnect’:
trendchip.c:1394: warning: implicit declaration of function ‘unregister_netdev’
trendchip.c:1400: warning: implicit declaration of function ‘usb_dec_dev_use’
trendchip.c:1403: warning: implicit declaration of function ‘usb_driver_release_interface’
trendchip.c:1404: error: dereferencing pointer to incomplete type
trendchip.c:1408: error: dereferencing pointer to incomplete type
trendchip.c: At top level:
trendchip.c:1421: error: variable ‘CDCEther_driver’ has initializer but incomplete type
trendchip.c:1422: error: unknown field ‘name’ specified in initializer
trendchip.c:1422: warning: excess elements in struct initializer
trendchip.c:1422: warning: (near initialization for ‘CDCEther_driver’)
trendchip.c:1423: error: unknown field ‘probe’ specified in initializer
trendchip.c:1423: warning: excess elements in struct initializer
trendchip.c:1423: warning: (near initialization for ‘CDCEther_driver’)
trendchip.c:1424: error: unknown field ‘disconnect’ specified in initializer
trendchip.c:1424: warning: excess elements in struct initializer
trendchip.c:1424: warning: (near initialization for ‘CDCEther_driver’)
trendchip.c:1425: error: unknown field ‘id_table’ specified in initializer
trendchip.c:1425: warning: excess elements in struct initializer
trendchip.c:1425: warning: (near initialization for ‘CDCEther_driver’)
trendchip.c:1432: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘CDCEther_init’
trendchip.c:1439: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘CDCEther_exit’
trendchip.c:1449: warning: data definition has no type or storage class
trendchip.c:1449: warning: type defaults to ‘int’ in declaration of ‘module_init’
trendchip.c:1449: warning: parameter names (without types) in function declaration
trendchip.c:1450: warning: data definition has no type or storage class
trendchip.c:1450: warning: type defaults to ‘int’ in declaration of ‘module_exit’
trendchip.c:1450: warning: parameter names (without types) in function declaration
trendchip.c:1452: error: expected declaration specifiers or ‘...’ before string constant
trendchip.c:1452: warning: data definition has no type or storage class
trendchip.c:1452: warning: type defaults to ‘int’ in declaration of ‘MODULE_AUTHOR’
trendchip.c:1453: error: expected declaration specifiers or ‘...’ before string constant
trendchip.c:1453: warning: data definition has no type or storage class
trendchip.c:1453: warning: type defaults to ‘int’ in declaration of ‘MODULE_DESCRIPTION’
trendchip.c:1454: error: expected declaration specifiers or ‘...’ before string constant
trendchip.c:1454: warning: data definition has no type or storage class
trendchip.c:1454: warning: type defaults to ‘int’ in declaration of ‘MODULE_LICENSE’
trendchip.c:1456: warning: data definition has no type or storage class
trendchip.c:1456: warning: type defaults to ‘int’ in declaration of ‘MODULE_DEVICE_TABLE’
trendchip.c:1456: warning: parameter names (without types) in function declaration
make: *** [trendchip.o] Error 1
[/I]

Please HELP.

I am being forced to use Windows for internet surfing.

Rakesh Gupta

---

### Post by khurrammirza on 2009-07-10
Can you upload your files given by MTNL to site like mediafire .I will try able to compile them & upload the binary or packageFor this your ubuntu should be i386(32 bit) as mine is also this & amd or intel.

Or you can also try copying(not cutting) files from /usr/src/linux-2.6.28-11-generic/include/linux to /usr/include/linux skipfiles you already have (.as I see you have header install otherwise this line must have given error gcc -Wall -D__KERNEL__ -DMODULE -I/usr/src/linux-2.6.28-11-generic/include -O -g -I.. -c -o trendchip.o trendchip.c.)

According to me MTNL is totally dumb if they cant give their customer binary file or packages like deb,rpm,pkg,blah,blah,blah.I am making them since I started using computer.I use config.,make install.for using software which I install from svn.

---

