---
title: "permission denied but im sudo why?"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by expxe on 2009-12-06
im trying to install my dwl-520+ wireless card and im following this guide: [http://www.houseofcraig.net/acx100_howto.php#trouble_compiling](http://www.houseofcraig.net/acx100_howto.php#trouble_compiling)

now when i get to Compiling the Driver section

i get an error and the solution in the troubleshooting section: echo -e '\nCONFIG_NET_WIRELESS=y\n' >> /lib/modules/`uname -r`/build/.config doesn't work

anyone know why?

here is the output

```
kernel version file: /lib/modules/2.6.31-16-generic/build/include/linux/version.h
Kernel configuration file: /lib/modules/2.6.31-16-generic/build/.config
Make damn sure these really match your currently running kernel!!

Kernel configuration found, performing sanity checks
All of the following items are required by the driver:
    Loadable modules support is enabled.
    Wireless LAN (non-hamradio) support is DISABLED!
    Wireless extensions support is DISABLED!
The following is needed for PCMCIA/CardBus cards:
    PCMCIA support is enabled.
    CardBus support is enabled.
The following is needed for USB card support:
    USB support is enabled.
The following is needed for PCI card support:
    PCI support is enabled.
Kernel configuration lacks needed options, please correct! ABORTING.
make: *** [config.mk] Error 1
henry@henry-desktop:~/acx100-0.2.0pre8_plus_fixes_57$ echo -e '\nCONFIG_NET_WIRELESS=y\n' >> /lib/modules/`uname -r`/build/.config
bash: /lib/modules/2.6.31-16-generic/build/.config: Permission denied
henry@henry-desktop:~/acx100-0.2.0pre8_plus_fixes_57$ sudo echo -e '\nCONFIG_NET_WIRELESS=y\n' >> /lib/modules/`uname -r`/build/.config
bash: /lib/modules/2.6.31-16-generic/build/.config: Permission denied

```

---

### Post by northd_tech on 2009-12-06
Try 
```
sudo su make
``` (or whatever command you were running after "sudo su")

A few people have noticed that "sudo su" will usually work if "sudo" doesn't.

---

### Post by expxe on 2009-12-06
sudo su echo -e '\nCONFIG_NET_WIRELESS=y\n' >> /lib/modules/`uname -r`/build/.config
bash: /lib/modules/2.6.31-16-generic/build/.config: Permission denied


sudo su make doesn't work either

---

### Post by Trumpen on 2009-12-06
redirection is done before the command "sudo echo ..." is executed; and it fails, because you are not root yet :)

Try with:

```
sudo bash -c "echo -e '\nCONFIG_NET_WIRELESS=y\n' >> /lib/modules/$(uname -r)/build/.config"
```

---

### Post by wojox on 2009-12-06
```
cat /lib/modules/2.6.31-16-generic/build/.config
```

#Automatically generated make config

---

### Post by expxe on 2009-12-06
> **Trumpen said:**
> redirection is done before the command "sudo echo ..." is executed; and it fails, because you are not root yet :)

Try with:

```
sudo bash -c "echo -e '\nCONFIG_NET_WIRELESS=y\n' >> /lib/modules/$(uname -r)/build/.config"
```
doesnt work, output is either 

the cursor with my name 
or 
a blank cursor and i have to restart terminal

> **northd_tech said:**
> Well if you want to activate the root password (which I believe can be the same as your normal "sudo" password for convenience), try:

```
sudo passwd root

su

```


After putting that password in 3 times, you should now be logged in as root.

Then cd to where the sourcecode that you were trying to make is located and run your commands again (as root this time).  I've had to do this while compiling wireless drivers before, and I believe that you can go in through System>Administration>Users & Groups and de-activate the root account from there (with your root and/or "sudo" password) after you've got your modules or whatever built.

i did this and retried the make, still doesn't work

> **wojox said:**
> ```
cat /lib/modules/2.6.31-16-generic/build/.config
```

#Automatically generated make config

here is the output...

```
# Pseudo filesystems
#
CONFIG_PROC_FS=y
CONFIG_PROC_KCORE=y
CONFIG_PROC_VMCORE=y
CONFIG_PROC_SYSCTL=y
CONFIG_PROC_PAGE_MONITOR=y
CONFIG_SYSFS=y
CONFIG_TMPFS=y
CONFIG_TMPFS_POSIX_ACL=y
CONFIG_HUGETLBFS=y
CONFIG_HUGETLB_PAGE=y
CONFIG_CONFIGFS_FS=m
CONFIG_MISC_FILESYSTEMS=y
CONFIG_ADFS_FS=m
# CONFIG_ADFS_FS_RW is not set
CONFIG_AFFS_FS=m
CONFIG_ECRYPT_FS=y
CONFIG_HFS_FS=m
CONFIG_HFSPLUS_FS=m
CONFIG_BEFS_FS=m
# CONFIG_BEFS_DEBUG is not set
CONFIG_BFS_FS=m
CONFIG_EFS_FS=m
CONFIG_JFFS2_FS=m
CONFIG_JFFS2_FS_DEBUG=0
CONFIG_JFFS2_FS_WRITEBUFFER=y
# CONFIG_JFFS2_FS_WBUF_VERIFY is not set
# CONFIG_JFFS2_SUMMARY is not set
# CONFIG_JFFS2_FS_XATTR is not set
CONFIG_JFFS2_COMPRESSION_OPTIONS=y
CONFIG_JFFS2_ZLIB=y
CONFIG_JFFS2_LZO=y
CONFIG_JFFS2_RTIME=y
# CONFIG_JFFS2_RUBIN is not set
# CONFIG_JFFS2_CMODE_NONE is not set
# CONFIG_JFFS2_CMODE_PRIORITY is not set
# CONFIG_JFFS2_CMODE_SIZE is not set
CONFIG_JFFS2_CMODE_FAVOURLZO=y
CONFIG_UBIFS_FS=m
CONFIG_UBIFS_FS_XATTR=y
# CONFIG_UBIFS_FS_ADVANCED_COMPR is not set
CONFIG_UBIFS_FS_LZO=y
CONFIG_UBIFS_FS_ZLIB=y
# CONFIG_UBIFS_FS_DEBUG is not set
CONFIG_CRAMFS=m
CONFIG_SQUASHFS=m
# CONFIG_SQUASHFS_EMBEDDED is not set
CONFIG_SQUASHFS_FRAGMENT_CACHE_SIZE=3
CONFIG_VXFS_FS=m
CONFIG_MINIX_FS=m
CONFIG_OMFS_FS=m
CONFIG_HPFS_FS=m
CONFIG_QNX4FS_FS=m
CONFIG_ROMFS_FS=m
CONFIG_ROMFS_BACKED_BY_BLOCK=y
# CONFIG_ROMFS_BACKED_BY_MTD is not set
# CONFIG_ROMFS_BACKED_BY_BOTH is not set
CONFIG_ROMFS_ON_BLOCK=y
CONFIG_SYSV_FS=m
CONFIG_UFS_FS=m
# CONFIG_UFS_FS_WRITE is not set
# CONFIG_UFS_DEBUG is not set
CONFIG_EXOFS_FS=m
# CONFIG_EXOFS_DEBUG is not set
CONFIG_NILFS2_FS=m
CONFIG_NETWORK_FILESYSTEMS=y
CONFIG_NFS_FS=m
CONFIG_NFS_V3=y
CONFIG_NFS_V3_ACL=y
CONFIG_NFS_V4=y
# CONFIG_NFS_V4_1 is not set
# CONFIG_NFS_FSCACHE is not set
CONFIG_NFSD=m
CONFIG_NFSD_V2_ACL=y
CONFIG_NFSD_V3=y
CONFIG_NFSD_V3_ACL=y
CONFIG_NFSD_V4=y
CONFIG_LOCKD=m
CONFIG_LOCKD_V4=y
CONFIG_EXPORTFS=m
CONFIG_NFS_ACL_SUPPORT=m
CONFIG_NFS_COMMON=y
CONFIG_SUNRPC=m
CONFIG_SUNRPC_GSS=m
CONFIG_SUNRPC_XPRT_RDMA=m
CONFIG_RPCSEC_GSS_KRB5=m
CONFIG_RPCSEC_GSS_SPKM3=m
CONFIG_SMB_FS=m
# CONFIG_SMB_NLS_DEFAULT is not set
CONFIG_CIFS=m
# CONFIG_CIFS_STATS is not set
CONFIG_CIFS_WEAK_PW_HASH=y
CONFIG_CIFS_UPCALL=y
CONFIG_CIFS_XATTR=y
CONFIG_CIFS_POSIX=y
# CONFIG_CIFS_DEBUG2 is not set
CONFIG_CIFS_DFS_UPCALL=y
CONFIG_CIFS_EXPERIMENTAL=y
CONFIG_NCP_FS=m
CONFIG_NCPFS_PACKET_SIGNING=y
CONFIG_NCPFS_IOCTL_LOCKING=y
CONFIG_NCPFS_STRONG=y
CONFIG_NCPFS_NFS_NS=y
CONFIG_NCPFS_OS2_NS=y
# CONFIG_NCPFS_SMALLDOS is not set
CONFIG_NCPFS_NLS=y
CONFIG_NCPFS_EXTRAS=y
CONFIG_CODA_FS=m
CONFIG_AFS_FS=m
# CONFIG_AFS_DEBUG is not set
# CONFIG_AFS_FSCACHE is not set
CONFIG_9P_FS=m

#
# Partition Types
#
CONFIG_PARTITION_ADVANCED=y
CONFIG_ACORN_PARTITION=y
# CONFIG_ACORN_PARTITION_CUMANA is not set
# CONFIG_ACORN_PARTITION_EESOX is not set
CONFIG_ACORN_PARTITION_ICS=y
# CONFIG_ACORN_PARTITION_ADFS is not set
# CONFIG_ACORN_PARTITION_POWERTEC is not set
CONFIG_ACORN_PARTITION_RISCIX=y
CONFIG_OSF_PARTITION=y
CONFIG_AMIGA_PARTITION=y
CONFIG_ATARI_PARTITION=y
CONFIG_MAC_PARTITION=y
CONFIG_MSDOS_PARTITION=y
CONFIG_BSD_DISKLABEL=y
CONFIG_MINIX_SUBPARTITION=y
CONFIG_SOLARIS_X86_PARTITION=y
CONFIG_UNIXWARE_DISKLABEL=y
CONFIG_LDM_PARTITION=y
# CONFIG_LDM_DEBUG is not set
CONFIG_SGI_PARTITION=y
CONFIG_ULTRIX_PARTITION=y
CONFIG_SUN_PARTITION=y
CONFIG_KARMA_PARTITION=y
CONFIG_EFI_PARTITION=y
CONFIG_SYSV68_PARTITION=y
CONFIG_NLS=y
CONFIG_NLS_DEFAULT="cp437"
CONFIG_NLS_CODEPAGE_437=m
CONFIG_NLS_CODEPAGE_737=m
CONFIG_NLS_CODEPAGE_775=m
CONFIG_NLS_CODEPAGE_850=m
CONFIG_NLS_CODEPAGE_852=m
CONFIG_NLS_CODEPAGE_855=m
CONFIG_NLS_CODEPAGE_857=m
CONFIG_NLS_CODEPAGE_860=m
CONFIG_NLS_CODEPAGE_861=m
CONFIG_NLS_CODEPAGE_862=m
CONFIG_NLS_CODEPAGE_863=m
CONFIG_NLS_CODEPAGE_864=m
CONFIG_NLS_CODEPAGE_865=m
CONFIG_NLS_CODEPAGE_866=m
CONFIG_NLS_CODEPAGE_869=m
CONFIG_NLS_CODEPAGE_936=m
CONFIG_NLS_CODEPAGE_950=m
CONFIG_NLS_CODEPAGE_932=m
CONFIG_NLS_CODEPAGE_949=m
CONFIG_NLS_CODEPAGE_874=m
CONFIG_NLS_ISO8859_8=m
CONFIG_NLS_CODEPAGE_1250=m
CONFIG_NLS_CODEPAGE_1251=m
CONFIG_NLS_ASCII=m
CONFIG_NLS_ISO8859_1=m
CONFIG_NLS_ISO8859_2=m
CONFIG_NLS_ISO8859_3=m
CONFIG_NLS_ISO8859_4=m
CONFIG_NLS_ISO8859_5=m
CONFIG_NLS_ISO8859_6=m
CONFIG_NLS_ISO8859_7=m
CONFIG_NLS_ISO8859_9=m
CONFIG_NLS_ISO8859_13=m
CONFIG_NLS_ISO8859_14=m
CONFIG_NLS_ISO8859_15=m
CONFIG_NLS_KOI8_R=m
CONFIG_NLS_KOI8_U=m
CONFIG_NLS_UTF8=m
CONFIG_DLM=m
# CONFIG_DLM_DEBUG is not set

#
# Kernel hacking
#
CONFIG_TRACE_IRQFLAGS_SUPPORT=y
CONFIG_PRINTK_TIME=y
# CONFIG_ENABLE_WARN_DEPRECATED is not set
# CONFIG_ENABLE_MUST_CHECK is not set
CONFIG_FRAME_WARN=1024
CONFIG_MAGIC_SYSRQ=y
CONFIG_UNUSED_SYMBOLS=y
CONFIG_DEBUG_FS=y
# CONFIG_HEADERS_CHECK is not set
CONFIG_DEBUG_KERNEL=y
# CONFIG_DEBUG_SHIRQ is not set
CONFIG_DETECT_SOFTLOCKUP=y
# CONFIG_BOOTPARAM_SOFTLOCKUP_PANIC is not set
CONFIG_BOOTPARAM_SOFTLOCKUP_PANIC_VALUE=0
CONFIG_DETECT_HUNG_TASK=y
# CONFIG_BOOTPARAM_HUNG_TASK_PANIC is not set
CONFIG_BOOTPARAM_HUNG_TASK_PANIC_VALUE=0
CONFIG_SCHED_DEBUG=y
CONFIG_SCHEDSTATS=y
CONFIG_TIMER_STATS=y
# CONFIG_DEBUG_OBJECTS is not set
# CONFIG_SLUB_DEBUG_ON is not set
# CONFIG_SLUB_STATS is not set
# CONFIG_DEBUG_KMEMLEAK is not set
# CONFIG_DEBUG_RT_MUTEXES is not set
# CONFIG_RT_MUTEX_TESTER is not set
# CONFIG_DEBUG_SPINLOCK is not set
# CONFIG_DEBUG_MUTEXES is not set
# CONFIG_DEBUG_LOCK_ALLOC is not set
# CONFIG_PROVE_LOCKING is not set
# CONFIG_LOCK_STAT is not set
# CONFIG_DEBUG_SPINLOCK_SLEEP is not set
# CONFIG_DEBUG_LOCKING_API_SELFTESTS is not set
CONFIG_STACKTRACE=y
# CONFIG_DEBUG_KOBJECT is not set
CONFIG_DEBUG_BUGVERBOSE=y
# CONFIG_DEBUG_INFO is not set
# CONFIG_DEBUG_VM is not set
# CONFIG_DEBUG_VIRTUAL is not set
# CONFIG_DEBUG_WRITECOUNT is not set
CONFIG_DEBUG_MEMORY_INIT=y
# CONFIG_DEBUG_LIST is not set
# CONFIG_DEBUG_SG is not set
# CONFIG_DEBUG_NOTIFIERS is not set
CONFIG_ARCH_WANT_FRAME_POINTERS=y
CONFIG_FRAME_POINTER=y
# CONFIG_BOOT_PRINTK_DELAY is not set
# CONFIG_RCU_TORTURE_TEST is not set
# CONFIG_RCU_CPU_STALL_DETECTOR is not set
# CONFIG_KPROBES_SANITY_TEST is not set
# CONFIG_BACKTRACE_SELF_TEST is not set
# CONFIG_DEBUG_BLOCK_EXT_DEVT is not set
# CONFIG_LKDTM is not set
# CONFIG_FAULT_INJECTION is not set
CONFIG_LATENCYTOP=y
CONFIG_SYSCTL_SYSCALL_CHECK=y
# CONFIG_DEBUG_PAGEALLOC is not set
CONFIG_USER_STACKTRACE_SUPPORT=y
CONFIG_NOP_TRACER=y
CONFIG_HAVE_FUNCTION_TRACER=y
CONFIG_HAVE_FUNCTION_GRAPH_TRACER=y
CONFIG_HAVE_FUNCTION_GRAPH_FP_TEST=y
CONFIG_HAVE_FUNCTION_TRACE_MCOUNT_TEST=y
CONFIG_HAVE_DYNAMIC_FTRACE=y
CONFIG_HAVE_FTRACE_MCOUNT_RECORD=y
CONFIG_HAVE_FTRACE_SYSCALLS=y
CONFIG_RING_BUFFER=y
CONFIG_EVENT_TRACING=y
CONFIG_CONTEXT_SWITCH_TRACER=y
CONFIG_TRACING=y
CONFIG_GENERIC_TRACER=y
CONFIG_TRACING_SUPPORT=y
CONFIG_FTRACE=y
# CONFIG_FUNCTION_TRACER is not set
# CONFIG_IRQSOFF_TRACER is not set
# CONFIG_SYSPROF_TRACER is not set
# CONFIG_SCHED_TRACER is not set
# CONFIG_FTRACE_SYSCALLS is not set
# CONFIG_BOOT_TRACER is not set
CONFIG_BRANCH_PROFILE_NONE=y
# CONFIG_PROFILE_ANNOTATED_BRANCHES is not set
# CONFIG_PROFILE_ALL_BRANCHES is not set
# CONFIG_POWER_TRACER is not set
# CONFIG_STACK_TRACER is not set
# CONFIG_KMEMTRACE is not set
# CONFIG_WORKQUEUE_TRACER is not set
CONFIG_BLK_DEV_IO_TRACE=y
# CONFIG_FTRACE_STARTUP_TEST is not set
# CONFIG_MMIOTRACE is not set
# CONFIG_RING_BUFFER_BENCHMARK is not set
# CONFIG_PROVIDE_OHCI1394_DMA_INIT is not set
# CONFIG_FIREWIRE_OHCI_REMOTE_DMA is not set
# CONFIG_DYNAMIC_DEBUG is not set
# CONFIG_DMA_API_DEBUG is not set
# CONFIG_SAMPLES is not set
CONFIG_HAVE_ARCH_KGDB=y
CONFIG_KGDB=y
CONFIG_KGDB_SERIAL_CONSOLE=y
# CONFIG_KGDB_TESTS is not set
CONFIG_HAVE_ARCH_KMEMCHECK=y
# CONFIG_KMEMCHECK is not set
CONFIG_STRICT_DEVMEM=y
# CONFIG_X86_VERBOSE_BOOTUP is not set
CONFIG_EARLY_PRINTK=y
# CONFIG_EARLY_PRINTK_DBGP is not set
# CONFIG_DEBUG_STACKOVERFLOW is not set
# CONFIG_DEBUG_STACK_USAGE is not set
# CONFIG_DEBUG_PER_CPU_MAPS is not set
# CONFIG_X86_PTDUMP is not set
CONFIG_DEBUG_RODATA=y
# CONFIG_DEBUG_RODATA_TEST is not set
# CONFIG_DEBUG_NX_TEST is not set
# CONFIG_IOMMU_DEBUG is not set
# CONFIG_IOMMU_STRESS is not set
CONFIG_HAVE_MMIOTRACE_SUPPORT=y
CONFIG_IO_DELAY_TYPE_0X80=0
CONFIG_IO_DELAY_TYPE_0XED=1
CONFIG_IO_DELAY_TYPE_UDELAY=2
CONFIG_IO_DELAY_TYPE_NONE=3
# CONFIG_IO_DELAY_0X80 is not set
CONFIG_IO_DELAY_0XED=y
# CONFIG_IO_DELAY_UDELAY is not set
# CONFIG_IO_DELAY_NONE is not set
CONFIG_DEFAULT_IO_DELAY_TYPE=1
# CONFIG_DEBUG_BOOT_PARAMS is not set
# CONFIG_CPA_DEBUG is not set
CONFIG_OPTIMIZE_INLINING=y

#
# Security options
#
CONFIG_KEYS=y
# CONFIG_KEYS_DEBUG_PROC_KEYS is not set
CONFIG_SECURITY=y
CONFIG_SECURITYFS=y
CONFIG_SECURITY_DEFAULT="apparmor"
CONFIG_SECURITY_NETWORK=y
# CONFIG_SECURITY_NETWORK_XFRM is not set
CONFIG_SECURITY_PATH=y
CONFIG_SECURITY_FILE_CAPABILITIES=y
# CONFIG_SECURITY_ROOTPLUG is not set
CONFIG_LSM_MMAP_MIN_ADDR=0
CONFIG_SECURITY_SELINUX=y
CONFIG_SECURITY_SELINUX_BOOTPARAM=y
CONFIG_SECURITY_SELINUX_BOOTPARAM_VALUE=0
CONFIG_SECURITY_SELINUX_DISABLE=y
CONFIG_SECURITY_SELINUX_DEVELOP=y
CONFIG_SECURITY_SELINUX_AVC_STATS=y
CONFIG_SECURITY_SELINUX_CHECKREQPROT_VALUE=1
# CONFIG_SECURITY_SELINUX_POLICYDB_VERSION_MAX is not set
CONFIG_SECURITY_SMACK=y
CONFIG_SECURITY_TOMOYO=y
# CONFIG_IMA is not set
CONFIG_XOR_BLOCKS=m
CONFIG_ASYNC_CORE=m
CONFIG_ASYNC_MEMCPY=m
CONFIG_ASYNC_XOR=m
CONFIG_CRYPTO=y

#
# Crypto core or helper
#
CONFIG_CRYPTO_FIPS=y
CONFIG_CRYPTO_ALGAPI=y
CONFIG_CRYPTO_ALGAPI2=y
CONFIG_CRYPTO_AEAD=m
CONFIG_CRYPTO_AEAD2=y
CONFIG_CRYPTO_BLKCIPHER=m
CONFIG_CRYPTO_BLKCIPHER2=y
CONFIG_CRYPTO_HASH=y
CONFIG_CRYPTO_HASH2=y
CONFIG_CRYPTO_RNG=m
CONFIG_CRYPTO_RNG2=y
CONFIG_CRYPTO_PCOMP=y
CONFIG_CRYPTO_MANAGER=y
CONFIG_CRYPTO_MANAGER2=y
CONFIG_CRYPTO_GF128MUL=m
CONFIG_CRYPTO_NULL=m
CONFIG_CRYPTO_WORKQUEUE=y
CONFIG_CRYPTO_CRYPTD=m
CONFIG_CRYPTO_AUTHENC=m
CONFIG_CRYPTO_TEST=m

#
# Authenticated Encryption with Associated Data
#
CONFIG_CRYPTO_CCM=m
CONFIG_CRYPTO_GCM=m
CONFIG_CRYPTO_SEQIV=m

#
# Block modes
#
CONFIG_CRYPTO_CBC=m
CONFIG_CRYPTO_CTR=m
CONFIG_CRYPTO_CTS=m
CONFIG_CRYPTO_ECB=m
CONFIG_CRYPTO_LRW=m
CONFIG_CRYPTO_PCBC=m
CONFIG_CRYPTO_XTS=m
CONFIG_CRYPTO_FPU=m

#
# Hash modes
#
CONFIG_CRYPTO_HMAC=y
CONFIG_CRYPTO_XCBC=m

#
# Digest
#
CONFIG_CRYPTO_CRC32C=m
CONFIG_CRYPTO_CRC32C_INTEL=m
CONFIG_CRYPTO_MD4=m
CONFIG_CRYPTO_MD5=y
CONFIG_CRYPTO_MICHAEL_MIC=m
CONFIG_CRYPTO_RMD128=m
CONFIG_CRYPTO_RMD160=m
CONFIG_CRYPTO_RMD256=m
CONFIG_CRYPTO_RMD320=m
CONFIG_CRYPTO_SHA1=m
CONFIG_CRYPTO_SHA256=m
CONFIG_CRYPTO_SHA512=m
CONFIG_CRYPTO_TGR192=m
CONFIG_CRYPTO_WP512=m

#
# Ciphers
#
CONFIG_CRYPTO_AES=m
CONFIG_CRYPTO_AES_X86_64=m
CONFIG_CRYPTO_AES_NI_INTEL=m
CONFIG_CRYPTO_ANUBIS=m
CONFIG_CRYPTO_ARC4=m
CONFIG_CRYPTO_BLOWFISH=m
CONFIG_CRYPTO_CAMELLIA=m
CONFIG_CRYPTO_CAST5=m
CONFIG_CRYPTO_CAST6=m
CONFIG_CRYPTO_DES=m
CONFIG_CRYPTO_FCRYPT=m
CONFIG_CRYPTO_KHAZAD=m
CONFIG_CRYPTO_SALSA20=m
CONFIG_CRYPTO_SALSA20_X86_64=m
CONFIG_CRYPTO_SEED=m
CONFIG_CRYPTO_SERPENT=m
CONFIG_CRYPTO_TEA=m
CONFIG_CRYPTO_TWOFISH=m
CONFIG_CRYPTO_TWOFISH_COMMON=m
CONFIG_CRYPTO_TWOFISH_X86_64=m

#
# Compression
#
CONFIG_CRYPTO_DEFLATE=m
CONFIG_CRYPTO_ZLIB=m
CONFIG_CRYPTO_LZO=m

#
# Random Number Generation
#
CONFIG_CRYPTO_ANSI_CPRNG=m
CONFIG_CRYPTO_HW=y
CONFIG_CRYPTO_DEV_PADLOCK=y
CONFIG_CRYPTO_DEV_PADLOCK_AES=m
CONFIG_CRYPTO_DEV_PADLOCK_SHA=m
CONFIG_CRYPTO_DEV_HIFN_795X=m
CONFIG_CRYPTO_DEV_HIFN_795X_RNG=y
CONFIG_HAVE_KVM=y
CONFIG_HAVE_KVM_IRQCHIP=y
CONFIG_VIRTUALIZATION=y
CONFIG_KVM=m
CONFIG_KVM_INTEL=m
CONFIG_KVM_AMD=m
# CONFIG_KVM_TRACE is not set
CONFIG_VIRTIO=m
CONFIG_VIRTIO_RING=m
CONFIG_VIRTIO_PCI=m
CONFIG_VIRTIO_BALLOON=m
CONFIG_BINARY_PRINTF=y

#
# Library routines
#
CONFIG_BITREVERSE=y
CONFIG_GENERIC_FIND_FIRST_BIT=y
CONFIG_GENERIC_FIND_NEXT_BIT=y
CONFIG_GENERIC_FIND_LAST_BIT=y
CONFIG_CRC_CCITT=m
CONFIG_CRC16=y
CONFIG_CRC_T10DIF=y
CONFIG_CRC_ITU_T=m
CONFIG_CRC32=y
CONFIG_CRC7=m
CONFIG_LIBCRC32C=m
CONFIG_ZLIB_INFLATE=y
CONFIG_ZLIB_DEFLATE=m
CONFIG_LZO_COMPRESS=m
CONFIG_LZO_DECOMPRESS=m
CONFIG_DECOMPRESS_GZIP=y
CONFIG_DECOMPRESS_BZIP2=y
CONFIG_DECOMPRESS_LZMA=y
CONFIG_GENERIC_ALLOCATOR=y
CONFIG_REED_SOLOMON=m
CONFIG_REED_SOLOMON_DEC16=y
CONFIG_TEXTSEARCH=y
CONFIG_TEXTSEARCH_KMP=m
CONFIG_TEXTSEARCH_BM=m
CONFIG_TEXTSEARCH_FSM=m
CONFIG_HAS_IOMEM=y
CONFIG_HAS_IOPORT=y
CONFIG_HAS_DMA=y
CONFIG_CHECK_SIGNATURE=y
CONFIG_NLATTR=y

CONFIG_NET_WIRELESS=y


CONFIG_NET_WIRELESS=y


CONFIG_NET_WIRELESS=y

```

---

### Post by sisco311 on 2009-12-06
> **expxe said:**
> doesnt work, output is either 

the cursor with my name 
or 
a blank cursor and i have to restart terminal



It worked (for 3 times). The command simply appends the file with *CONFIG_NET_WIRELESS=y*.

Edit the file:
```
gksu gedit /lib/modules/`uname -r`/build/.config
```
and remove the duplicate entries. 

[uhelp]community/RootSudo[/uhelp]

Next time use something like:
```
echo -e "new line" | sudo tee -a /path/to/file
```

---

### Post by expxe on 2009-12-06
> **sisco311 said:**
> It worked (for 3 times). The command simply appends the file with *CONFIG_NET_WIRELESS=y*.

Edit the file:
```
gksu gedit /lib/modules/`uname -r`/build/.config
```
and remove the duplicate entries. 

[uhelp]community/RootSudo[/uhelp]

Next time use something like:
```
echo -e "new line" | sudo tee -a /path/to/file
```

can you please connect your instructions to the guide

im at "First, change to the acx100-0.2.0pre8_plus_fixes_57 top-level directory, type: cd /home/your_normal_username/acx100-0.2.0pre8_plus_fixes_57. "

and this step fails: "make"

so what exactly do i next?

---

### Post by sisco311 on 2009-12-06
> **expxe said:**
> 
i did this and retried the make, still doesn't work


You should not enable the root account until you  know exactly what are you doing.

To re-disable it, run:
```
sudo usermod -p '!' root
```

To simulate a root login shell you can run:
```
sudo -i
```

To exit from the shell type:```
exit
```or press Ctrl+d.

Please read the community documentation about sudo (link in my first post).

---

### Post by sisco311 on 2009-12-06
> **expxe said:**
> can you please connect your instructions to the guide

im at "First, change to the acx100-0.2.0pre8_plus_fixes_57 top-level directory, type: cd /home/your_normal_username/acx100-0.2.0pre8_plus_fixes_57. "

and this step fails: "make"

so what exactly do i next?

Okay, lets start from the beginning. What's the output of:
```
lspci
```

---

### Post by expxe on 2009-12-06
if you are gonna help me out now ill stay here and try to reply within one-two min between posts

im trying to install a dlink dwl-520+, it is fully supported according to here: [http://acx100.sourceforge.net/matrix.html](http://acx100.sourceforge.net/matrix.html)
so i could try installing this driver or i could try the latest one at sourceforge, i also posted a topic on that issue here: [http://ubuntuforums.org/showthread.php?t=1347945](http://ubuntuforums.org/showthread.php?t=1347945)

which issue is easier to solve? i can move on to the easier one

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. Device 9602
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:06.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
04:07.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
04:07.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
04:07.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)

```

---

### Post by chili555 on 2009-12-06
Post #1 here compiles without error for me running Karmic. [http://ubuntuforums.org/showthread.php?t=1321303](http://ubuntuforums.org/showthread.php?t=1321303)

I don't have the device to test it, however, the module insmodded without complaint. I think the Karmic patch is the key.

It will be a bit tricky to get the module loaded automagically on boot; let us know your result and post back for help.

---

### Post by expxe on 2009-12-06
> **chili555 said:**
> Post #1 here compiles without error for me running Karmic. [http://ubuntuforums.org/showthread.php?t=1321303](http://ubuntuforums.org/showthread.php?t=1321303)

I don't have the device to test it, however, the module insmodded without complaint. I think the Karmic patch is the key.

It will be a bit tricky to get the module loaded automagically on boot; let us know your result and post back for help.

> mkdir acx
cd acx
wget [http://downloads.sourceforge.net/acx...080210.tar.bz2](http://downloads.sourceforge.net/acx...080210.tar.bz2)
tar xjvf acx-20080210.tar.bz2
wget [http://cc.oulu.fi/~rantalai/acx_karmic.patch](http://cc.oulu.fi/~rantalai/acx_karmic.patch)
patch -p0 < acx_karmic.patch
cd acx-20080210/
make -C /lib/modules/`uname -r`/build M=`pwd`

Load de kernel module
sudo insmod acx.ko

i got midway thru and this is the output

```
make -C /lib/modules/`uname -r`/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  LD      /home/henry/acx/acx-20080210/built-in.o
  CC [M]  /home/henry/acx/acx-20080210/wlan.o
  CC [M]  /home/henry/acx/acx-20080210/conv.o
/home/henry/acx/acx-20080210/conv.c: In function &#8216;acx_rxbuf_to_ether&#8217;:
/home/henry/acx/acx-20080210/conv.c:502: warning: cast from pointer to integer of different size
  CC [M]  /home/henry/acx/acx-20080210/ioctl.o
  CC [M]  /home/henry/acx/acx-20080210/common.o
/home/henry/acx/acx-20080210/common.c: In function &#8216;acx_s_proc_diag_output&#8217;:
/home/henry/acx/acx-20080210/common.c:1249: warning: format &#8216;%u&#8217; expects type &#8216;unsigned int&#8217;, but argument 4 has type &#8216;long unsigned int&#8217;
/home/henry/acx/acx-20080210/common.c:1527: warning: cast from pointer to integer of different size
/home/henry/acx/acx-20080210/common.c:1527: warning: cast from pointer to integer of different size
/home/henry/acx/acx-20080210/common.c:1532: warning: cast from pointer to integer of different size
/home/henry/acx/acx-20080210/common.c:1532: warning: cast from pointer to integer of different size
  CC [M]  /home/henry/acx/acx-20080210/pci.o
  CC [M]  /home/henry/acx/acx-20080210/usb.o
  LD [M]  /home/henry/acx/acx-20080210/acx.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: Found 3 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /home/henry/acx/acx-20080210/acx.mod.o
  LD [M]  /home/henry/acx/acx-20080210/acx.ko
make: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'

```

btw, what is Load de kernel module?

i hope this works

---

### Post by chili555 on 2009-12-06
You didn't see the word 'error' did you? Please proceed.

The original poster meant 'Load **the** kernel module' by insmodding it.```
sudo insmod acx.ko 
```Not many people spell well on the internet, even me!!!

---

### Post by expxe on 2009-12-06
> **chili555 said:**
> You didn't see the word 'error' did you? Please proceed.

The original poster meant 'Load **the** kernel module' by insmodding it.```
sudo insmod acx.ko 
```Not many people spell well on the internet, even me!!!
done, so now how do i check for wireless? i have wicd installed and network-manager uninstalled

i unplugged my ethernet and that just results in no internet....

---

### Post by chili555 on 2009-12-06
Please let us see:```
lsmod | grep acx
iwconfig
```Thanks.

---

### Post by expxe on 2009-12-06
henry@henry-desktop:~$ lsmod | grep acx
acx                   158440  0 
henry@henry-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

henry@henry-desktop:~$ 


and acx is in red

---

### Post by chili555 on 2009-12-06
Please do:```
cd ~
dmesg > dmesg.txt
zip -r dmesg.zip dmesg.txt
```Please attach *dmesg.zip* to a reply.

---

### Post by chili555 on 2009-12-06
> acx: compiled to use [COLOR="Red"]32bit[/COLOR] I/O access.> PROUDLY UBUNTING MY COMPUTER SINCE 2009 - Karmic Koala 9.10 [COLOR="Red"]64 Bit[/COLOR]This could be a conflict...

---

### Post by expxe on 2009-12-06
> **chili555 said:**
> Please do:```
cd ~
dmesg > dmesg.txt
zip -r dmesg.zip dmesg.txt
```Please attach *dmesg.zip* to a reply.

i copied each line one by one, now where do i find this zip file?

```
henry@henry-desktop:~$ cd ~
henry@henry-desktop:~$ dmesg > dmesg.txt
henry@henry-desktop:~$ zip -r dmesg.zip dmesg.txt
  adding: dmesg.txt (deflated 92%)

```

---

### Post by chili555 on 2009-12-06
It will be in your Home folder.

---

### Post by expxe on 2009-12-06
attached

---

### Post by chili555 on 2009-12-06
There are about a zillion of these:> [12799.806979] VFS: busy inodes on changed media or resized disk sr0You would help your system by googling and fixing this. You also might start a new thred in 'General Help.'

Here is the next and, hopefully, last problem:> requesting firmware image 'tiacx100cFF'
[10709.246672] acx_pci 0000:04:06.0: firmware: requesting tiacx100cFF
[10709.301298] acx: firmware image 'tiacx100cFF' was not provided. Check your hotplug scripts
[10709.301307] requesting firmware image 'tiacx100'
[10709.301314] acx_pci 0000:04:06.0: firmware: requesting tiacx100
[10709.308195] acx: firmware image 'tiacx100' was not provided. Check your hotplug scriptsYou can fix this with:```
sudo apt-get install linux-firmware
cd acx/acx-20080210/
sudo rmmod -f acx.ko
sudo insmod acx.ko
iwconfig
```*Now*, do you have an interface?

Again, we will have to do some additional work to get this to come up on boot, once we figure it out for the first time!

---

### Post by expxe on 2009-12-06
i got:

```
henry@henry-desktop:~$ sudo apt-get install linux-firmware
[sudo] password for henry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.
The following packages were automatically installed and are no longer required:
  libnautilus-burn4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
henry@henry-desktop:~$ cd acx/acx-20080210/
henry@henry-desktop:~/acx/acx-20080210$ sudo rmmod -f acx.ko
henry@henry-desktop:~/acx/acx-20080210$ sudo insmod acx.ko
henry@henry-desktop:~/acx/acx-20080210$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

henry@henry-desktop:~/acx/acx-20080210$ 
```

---

### Post by chili555 on 2009-12-06
That dirty dog! Please try:```
sudo depmod -ae
sudo cp /lib/firmware/acx/default/tiacx100 /lib/firmware
sudo rmmod -f acx.ko
sudo insmod acx.ko
iwconfig
```If there is no interface, wlan0, perhaps, please give me another dmesg.zip as above.

---

### Post by expxe on 2009-12-06
after the first line i got

WARNING: -e needs -E or -F

continue?

```
henry@henry-desktop:~$ sudo depmod -ae
WARNING: -e needs -E or -Fhenry@henry-desktop:~$ sudo cp /lib/firmware/acx/default/tiacx100 /lib/firmware
henry@henry-desktop:~$ sudo rmmod -f acx.ko
ERROR: Removing 'acx': No such file or directory
henry@henry-desktop:~$ sudo insmod -f acx.ko
insmod: can't read 'acx.ko': No such file or directory
henry@henry-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

henry@henry-desktop:~$ 

```

---

### Post by expxe on 2009-12-06
im gonna have to call it night ill check back here tmr for any updates

edit: here is another zip file, taken after my last post

---

### Post by chili555 on 2009-12-06
The depmod continued on its own. Please do:```
cd acx/acx-20080210/
sudo rmmod -f acx.ko
sudo insmod acx.ko
iwconfig
```

---

### Post by expxe on 2009-12-06
> **chili555 said:**
> The depmod continued on its own. Please do:```
cd acx/acx-20080210/
sudo rmmod -f acx.ko
sudo insmod acx.ko
iwconfig
```

henry@henry-desktop:~$ cd acx/acx-20080210/
henry@henry-desktop:~/acx/acx-20080210$ sudo rmmod -f acx.ko
[sudo] password for henry: 
ERROR: Removing 'acx': No such file or directory
henry@henry-desktop:~/acx/acx-20080210$ sudo insmod acx.ko
henry@henry-desktop:~/acx/acx-20080210$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

henry@henry-desktop:~/acx/acx-20080210$

---

### Post by chili555 on 2009-12-06
> **expxe said:**
> im gonna have to call it night ill check back here tmr for any updates

edit: here is another zip file, taken after my last postNothing attached. See you tomorrow.

---

### Post by expxe on 2009-12-06
> **chili555 said:**
> Nothing attached. See you tomorrow.

i edited my post

---

### Post by expxe on 2009-12-09
hi again

any updates? 

im tempted to just stick with my wired connection but seeing that this card is fully supported in linux i feel that there must be something that can be done. is it normally this involved to get a wireless card working under linux?

---

### Post by chili555 on 2009-12-10
Did you see this? [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/495077](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/495077)

Your last dmesg still shows that the firmware is not getting loaded. Please try this. ```
cd acx/acx-20080210/
sudo rmmod -f acx.ko
sudo cp /lib/firmware/acx/1.9.8.b/tiacx100 /lib/firmware/
sudo cp /lib/firmware/acx/1.9.8.b/tiacx100r0D /lib/firmware/
sudo insmod acx.ko
iwconfig
```Now do you have an interface?

---

### Post by expxe on 2009-12-10
this is what i got so far, i take it this is good? never seen this before.

```
henry@henry-desktop:~$ cd acx/acx-20080210/
henry@henry-desktop:~/acx/acx-20080210$ sudo rmmod -f acx.ko
[sudo] password for henry: 
ERROR: Removing 'acx': No such file or directory
henry@henry-desktop:~/acx/acx-20080210$ sudo cp /lib/firmware/acx/1.9.8.b/tiacx100 /lib/firmware/
henry@henry-desktop:~/acx/acx-20080210$ sudo cp /lib/firmware/acx/1.9.8.b/tiacx100r0D /lib/firmware/
henry@henry-desktop:~/acx/acx-20080210$ sudo insmod acx.ko
henry@henry-desktop:~/acx/acx-20080210$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"STA1C9027"  Nickname:"acx v0.3.37"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:22 Mb/s   Tx-Power=18 dBm   Sensitivity=176/255  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

henry@henry-desktop:~/acx/acx-20080210$ 

```

---

