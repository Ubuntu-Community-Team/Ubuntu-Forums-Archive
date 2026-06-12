---
title: "NFS Server issues on Ubutu 10.4"
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by bertszoghy on 2011-02-22
Hello,

We are doing embedded Linux development on a new ARM eval board. On boot, the board downloads the kernel from a TFTP server on the host Ubuntu 10.4 box (works flawlessly) and then mounts its root file system through an NFS server which is also running on the same Ubuntu 10.4 box.

My problem is the NFS Server, it is flaky and quite unreliable. The board regularly stalls as it is booting the root file system after it finds it its root file system on the NFS Server all right, with "Configuring network interfaces: nfs: server 10.75.6.41 not responding, still trying" (see complete listing below). I also get a lot of errors such as, "NFS: server 10.75.6.41 error: fileid changed".

To add insult to injury, the board boots fine once in a while during the lunch hour or at the end of the work day when the corporate network might be less busy. Even then, when it does boot, and I can log in to it, I get errors that point to NFS troubles such as "ls: /libexec: Unknown 521".


According to [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

There are three configuration files that relate to an NFSv4 server: /etc/default/nfs-kernel-server, /etc/default/nfs-common and /etc/exports. 

My config files:




# BEGIN BLOCK /etc/default/nfs-kernel-server
    # Number of servers to start up
    RPCNFSDCOUNT=8
    
    # Runtime priority of server (see nice(1))
    RPCNFSDPRIORITY=0
    
    # Options for rpc.mountd.
    # If you have a port-based firewall, you might want to set up
    # a fixed port here using the --port option. For more information, 
    # see rpc.mountd(8) or [http://wiki.debian.org/?SecuringNFS](http://wiki.debian.org/?SecuringNFS)
    RPCMOUNTDOPTS=--manage-gids
    
    # Do you want to start the svcgssd daemon? It is only required for Kerberos
    # exports. Valid alternatives are "yes" and "no"; the default is "no".
    NEED_SVCGSSD=
    
    # Options for rpc.svcgssd.
    RPCSVCGSSDOPTS=
# END BLOCK /etc/default/nfs-kernel-server





# BEGIN BLOCK /etc/default/nfs-common
    # If you do not set values for the NEED_ options, they will be attempted
    # autodetected; this should be sufficient for most people. Valid alternatives
    # for the NEED_ options are "yes" and "no".

    # Do you want to start the statd daemon? It is not needed for NFSv4.
    NEED_STATD=

    # Options for rpc.statd.
    #   Should rpc.statd listen on a specific port? This is especially useful
    #   when you have a port-based firewall. To use a fixed port, set this
    #   this variable to a statd argument like: "--port 4000 --outgoing-port 4001".
    #   For more information, see rpc.statd(8) or [http://wiki.debian.org/?SecuringNFS](http://wiki.debian.org/?SecuringNFS)
    STATDOPTS=

    # Do you want to start the idmapd daemon? It is only needed for NFSv4.
    NEED_IDMAPD=

    # Do you want to start the gssd daemon? It is required for Kerberos mounts.
    NEED_GSSD=
# END BLOCK /etc/default/nfs-common





# BEGIN BLOCK /etc/exports
    # /etc/exports: the access control list for filesystems which may be exported
    #		to NFS clients.  See exports(5).
    #
    # Example for NFSv2 and NFSv3:
    # /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
    #
    # Example for NFSv4:
    # /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
    # /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
    #
    /tftpboot *(rw,no_root_squash,async)
# END BLOCK /etc/exports





Here is a listing of the board booting over Cutecom.






# BEGIN BLOCK Cutecom listing 

    U-Boot 2009.08 (Dec 23 2010 - 09:35:01)

    CPU:   454 MHz
    BUS:   151 MHz
    EMI:   205 MHz
    Board: 
    DRAM:  128 MB
    MMC:   IMX_SSP_MMC: 0, IMX_SSP_MMC: 1
    In:    serial
    Out:   serial
    Err:   serial
    Net:   got MAC address from IIM: 00:0c:c6:76:d1:3c
    FEC0
    Hit any key to stop autoboot:  3  2 1 0 
    BOOTP broadcast 1
    FEC: Link is down 7809
    BOOTP broadcast 2
    DHCP client bound to address 10.75.6.42
    Using FEC0 device
    TFTP from server 10.75.6.41; our IP address is 10.75.6.42
    Filename 'uImage_tx28'.
    Load address: 0x42000000
    Loading: *#################################################################
         #################################################################
         ########################
    done
    Bytes transferred = 2258104 (2274b8 hex)
    ## Booting kernel from Legacy Image at 42000000 ...
       Image Name:   Linux-2.6.37-rc6-karo
       Image Type:   ARM Linux Kernel Image (uncompressed)
       Data Size:    2258040 Bytes =  2.2 MB
       Load Address: 40008000
       Entry Point:  40008000
       Verifying Checksum ... OK
       Loading Kernel Image ... OK
    OK

    Starting kernel ...

    Linux version 2.6.37-rc6-karo (lothar@ipc1) (gcc version 4.4.1 (GCC) ) #1 PREEMPT Wed Dec 22 15:19:39 CET 2010
    CPU: ARM926EJ-S [41069265] revision 5 (ARMv5TEJ), cr=00053177
    CPU: VIVT data cache, VIVT instruction cache
    Machine: Ka-Ro electronics TX28 module
    Memory policy: ECC disabled, Data cache writeback
    On node 0 totalpages: 32768
    free_area_init_node: node 0, pgdat c045ad20, node_mem_map c099a000
      Normal zone: 288 pages used for memmap
      Normal zone: 0 pages reserved
      Normal zone: 32480 pages, LIFO batch:7
    pcpu-alloc: s0 r0 d32768 u32768 alloc=1*32768

    pcpu-alloc: [0] 0 
    Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 32480
    Kernel command line: init=/linuxrc root=/dev/nfs nfsroot=10.75.6.41:/tftpboot/rootfs,rsize=1024,wsize=1024,nolock debug panic=1 ip=10.75.6.66 console=ttyAM0,115200 rw
    PID hash table entries: 512 (order: -1, 2048 bytes)
    Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
    Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
    Memory: 128MB = 128MB total
    Memory: 119944k/119944k available, 11128k reserved, 0K highmem
    Virtual kernel memory layout:
        vector  : 0xffff0000 - 0xffff1000   (   4 kB)
        fixmap  : 0xfff00000 - 0xfffe0000   ( 896 kB)
        DMA     : 0xffc00000 - 0xffe00000   (   2 MB)
        vmalloc : 0xc8800000 - 0xf4000000   ( 696 MB)
        lowmem  : 0xc0000000 - 0xc8000000   ( 128 MB)
        modules : 0xbf000000 - 0xc0000000   (  16 MB)
          .init : 0xc0008000 - 0xc0032000   ( 168 kB)
          .text : 0xc0032000 - 0xc042929c   (4061 kB)
          .data : 0xc042a000 - 0xc045b4a0   ( 198 kB)
    SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
    Preemptable hierarchical RCU implementation.
        RCU-based detection of stalled CPUs is disabled.
        Verbose stalled-CPUs detection is disabled.
    NR_IRQS:304
    MXS GPIO hardware
    mxs_set_mode: changing mode from CLOCK_EVT_MODE_UNUSED to CLOCK_EVT_MODE_SHUTDOWN
    mxs_set_mode: changing mode from CLOCK_EVT_MODE_SHUTDOWN to CLOCK_EVT_MODE_ONESHOT
    Console: colour dummy device 80x30
    Lock dependency validator: Copyright (c) 2006 Red Hat, Inc., Ingo Molnar
    ... MAX_LOCKDEP_SUBCLASSES:  8
    ... MAX_LOCK_DEPTH:          48
    ... MAX_LOCKDEP_KEYS:        8191
    ... CLASSHASH_SIZE:          4096
    ... MAX_LOCKDEP_ENTRIES:     16384
    ... MAX_LOCKDEP_CHAINS:      32768
    ... CHAINHASH_SIZE:          16384

     memory used by lock dependency info: 3695 kB
     per task-struct memory footprint: 1152 bytes
    Calibrating delay loop... 226.09 BogoMIPS (lpj=1130496)
    pid_max: default: 32768 minimum: 301
    Mount-cache hash table entries: 512
    CPU: Testing write buffer coherency: ok
    devtmpfs: initialized
    regulator: core version 0.5
    regulator: dummy: 
    NET: Registered protocol family 16
    tx28_init_machine: Registering leds-gpio device
    tx28_init_machine: Registering i2c-gpio device
    tx28_i2c0_register: Registering I2C0 bus
    mxs_gpio_set_irq_type: set GPIO 73 to high trigger
    tx28_fec_gpio_init: Switching FEC PHY power off
    tx28_fec_gpio_init: Switching FEC PHY power on
    tx28_fec_gpio_init: Deasserting FEC PHY RESET
    tx28_fec_gpio_init: Registering FEC device
    bio: create slab <bio-0> at 0
    i2c-gpio i2c-gpio.0: using pins 121 (SDA) and 120 (SCL)
    Switching to clocksource mxs_timer
    Switched to NOHz mode on CPU #0
    NET: Registered protocol family 2
    IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
    TCP established hash table entries: 4096 (order: 3, 32768 bytes)
    TCP bind hash table entries: 4096 (order: 5, 147456 bytes)
    TCP: Hash tables configured (established 4096 bind 4096)
    TCP reno registered
    UDP hash table entries: 64 (order: 0, 5120 bytes)
    UDP-Lite hash table entries: 64 (order: 0, 5120 bytes)
    NET: Registered protocol family 1
    RPC: Registered udp transport module.
    RPC: Registered tcp transport module.
    RPC: Registered tcp NFSv4.1 backchannel transport module.
    NetWinder Floating Point Emulator V0.97 (double precision)
    JFFS2 version 2.2. (NAND) (SUMMARY)  © 2001-2006 Red Hat, Inc.
    msgmni has been set to 234
    alg: No test for stdrng (krng)
    Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
    io scheduler noop registered
    io scheduler deadline registered
    io scheduler cfq registered (default)
    mxs-duart.0: ttyAM0 at MMIO 0x80074000 (irq = 47) is a DebugUART
    console [ttyAM0] enabled
    brd: module loaded
    FEC Ethernet Driver
    fec_enet_mii_bus: probed
    net eth0: MAC addr: 00:0c:c6:76:d1:3c
    mice: PS/2 mouse device common for all mice
    rtc-ds1307 0-0068: SET TIME!
    rtc-ds1307 0-0068: rtc core: registered ds1339 as rtc0
    tx28_mmc_get_cd: SD CD=1
    mmc_spi spi0.0: SD/MMC host mmc0, no DMA, no WP, no poweroff
    Registered led device: GPIO-LED
    TCP cubic registered
    NET: Registered protocol family 17
    can: controller area network core (rev 20090105 abi 8)
    NET: Registered protocol family 29
    Registering the dns_resolver key type
    kmemleak: Kernel memory leak detector initialized
    kmemleak: Automatic memory scanning thread started
    rtc-ds1307 0-0068: setting system clock to 2000-01-06 02:32:36 UTC (947125956)
    net eth0: Freescale FEC PHY driver [SMSC LAN8710/LAN8720] (mii_bus:phy_addr=1:00, irq=-1)
    IP-Config: Guessing netmask 255.0.0.0
    IP-Config: Complete:
         device=eth0, addr=10.75.6.66, mask=255.0.0.0, gw=255.255.255.255,
         host=10.75.6.66, domain=, nis-domain=(none),
         bootserver=255.255.255.255, rootserver=10.75.6.41, rootpath=
    PHY: 1:00 - Link is Up - 100/Full
    VFS: Mounted root (nfs filesystem) on device 0:14.
    devtmpfs: mounted
    Freeing init memory: 168K
    Executing /sbin/init
    INIT:version 2.86 booting
    Starting the hotplug events dispatcher: udevdudevd (474): /proc/474/oom_adj is deprecated, please use /proc/474/oom_score_adj instead.

    udev: starting version 141
    Synthesizing the initial hotplug events...input: TSC2007 Touchscreen as /devices/virtual/input/input0
    done.
    Waiting for /dev to be fully populated...done.
    Activating swap...done.
    Initializing /var... Done.
    Loading kernel modules...done.
    Checking file systems...fsck from util-linux-ng 2.16
    done.
    INIT: Entering run level: 2

    Starting internet superserver: inetd done.
    Configuring network interfaces: nfs: server 10.75.6.41 not responding, still trying
    nfs: server 10.75.6.41 not responding, still trying

# END BLOCK Cutecom listing 




Permissions in my /tftpboot directory:

drwxrwxrwx  7 nobody   users        4096 2011-02-21 11:36 .
drwxr-xr-x 24 root     root         4096 2011-01-27 13:24 ..
drwxr-xr-x 20 root     root         4096 2010-12-22 09:18 rootfs
-rwxrwxrwx  1 bertrand bertrand  2258104 2011-02-17 09:06 uImage_tx28


Permissions in my /tftpboot/rootfs directory:
drwxr-xr-x 20 root   root     4096 2010-12-22 09:18 .
drwxrwxrwx  7 nobody users    4096 2011-02-21 11:36 ..
drwxr-sr-x  2 root   root     4096 2011-02-18 17:13 bin
drwxr-xr-x  2 root   root     4096 2010-08-20 14:23 data
drwxr-sr-x  2 root   root     4096 2010-08-20 17:48 dev
drwxr-sr-x 20 root   root     4096 2010-12-22 09:14 etc
drwxr-sr-x  4 root   root     4096 2009-12-07 07:30 home
drwxr-sr-x  8 root   root     4096 2010-08-20 17:48 lib
drwxr-sr-x  2 root   root     4096 2010-08-20 17:48 libexec
-rwxr-xr-x  1 root   root       63 2010-08-23 07:03 linuxrc
drwxr-xr-x  2 root   root     4096 2010-08-20 14:23 mnt
drwxr-xr-x  2 root   root     4096 2011-02-21 15:58 proc
drwxr-sr-x  2 root   root     4096 2010-12-21 05:51 root
-rwxr-xr-x  1 root   root  7093608 2011-02-18 15:40 rootfs_tx28.tgz
drwxr-sr-x  2 root   root     4096 2010-08-20 17:48 sbin
drwxr-xr-x  2 root   root     4096 2010-08-20 14:23 sdcard1
drwxr-xr-x  2 root   root     4096 2010-08-20 14:23 sdcard2
drwxr-xr-x  2 root   root     4096 2010-08-20 14:23 sys
-rw-r--r--  1 root   root       29 2010-12-22 09:18 .timestamp
drwxr-xr-x  2 root   root     4096 2010-08-20 14:23 tmp
drwxr-xr-x  2 root   root     4096 2010-08-20 14:23 usbdisk
drwxr-sr-x  8 root   root     4096 2010-05-21 12:35 usr
drwxr-sr-x  8 root   root     4096 2009-12-07 07:30 var





Any help greatly appreciated!!!

Bert

---

### Post by pmsoft1 on 2011-02-27
I have the same issue:
I'm trying to boot Ubuntu via PXE, the error I get
```
nfs: server 192.168.1.1 not responding, still trying
```

I can mount the nfs share from my Ubuntu desktop just fine.

---

### Post by bertszoghy on 2011-02-28
Hello,

Try modifying /etc/network/interfaces to make the IP static, and to match what you are providing as a param to the kernel in the board's boot loader.

Something like:

iface eth0 inet static
	address 192.168.1.241
	netmask 255.255.255.0


must be a tab and not spaces before "address" and "netmask".

B

---

