---
title: "Cannot install Alsa 82xx sound driver in Ubuntu 8.04"
date: 2009-03-19
forum: Multimedia Software
---

### Post by frozenade on 2009-03-19
Hi all..

I use ubuntu 8.04. My sound device is VIA onboard. I downloaded VIA driver from alsa-project.

but when I did "make", here's come:

```

/usr/src/linux/include/linux/fs.h:1499: error: âstruct inodeâ has no member named âi_sbâ
/usr/src/linux/include/linux/fs.h: At top level:
/usr/src/linux/include/linux/fs.h:1509: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h:1509: error: expected declaration specifiers or â...â before âsize_tâ
/usr/src/linux/include/linux/fs.h:1513: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h: In function âlocks_verify_truncateâ:
/usr/src/linux/include/linux/fs.h:1515: error: âstruct inodeâ has no member named âi_flockâ
/usr/src/linux/include/linux/fs.h:1518: error: âsizeâ undeclared (first use in this function)
/usr/src/linux/include/linux/fs.h:1518: error: âstruct inodeâ has no member named âi_sizeâ
/usr/src/linux/include/linux/fs.h:1518: error: âstruct inodeâ has no member named âi_sizeâ
/usr/src/linux/include/linux/fs.h:1519: error: âstruct inodeâ has no member named âi_sizeâ
/usr/src/linux/include/linux/fs.h:1519: error: âstruct inodeâ has no member named âi_sizeâ
/usr/src/linux/include/linux/fs.h:1520: error: âstruct inodeâ has no member named âi_sizeâ
/usr/src/linux/include/linux/fs.h:1521: error: too many arguments to function âlocks_mandatory_areaâ
/usr/src/linux/include/linux/fs.h: In function âbreak_leaseâ:
/usr/src/linux/include/linux/fs.h:1527: error: âstruct inodeâ has no member named âi_flockâ
/usr/src/linux/include/linux/fs.h: At top level:
/usr/src/linux/include/linux/fs.h:1534: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h:1595: error: expected â)â before â*â token
/usr/src/linux/include/linux/fs.h:1596: error: expected â)â before âunsignedâ
/usr/src/linux/include/linux/fs.h:1600: error: expected â)â before âunsignedâ
/usr/src/linux/include/linux/fs.h:1602: error: expected declaration specifiers or â...â before âoff_tâ
/usr/src/linux/include/linux/fs.h:1619: error: expected declaration specifiers or â...â before âumode_tâ
/usr/src/linux/include/linux/fs.h:1619: error: expected declaration specifiers or â...â before âdev_tâ
/usr/src/linux/include/linux/fs.h: In function âinvalidate_remote_inodeâ:
/usr/src/linux/include/linux/fs.h:1661: error: âstruct inodeâ has no member named âi_modeâ
/usr/src/linux/include/linux/fs.h:1661: error: âstruct inodeâ has no member named âi_modeâ
/usr/src/linux/include/linux/fs.h:1662: error: âstruct inodeâ has no member named âi_modeâ
/usr/src/linux/include/linux/fs.h:1663: error: âstruct inodeâ has no member named âi_mappingâ
/usr/src/linux/include/linux/fs.h: At top level:
/usr/src/linux/include/linux/fs.h:1674: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h:1674: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h:1678: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h:1678: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h: In function âput_write_accessâ:
/usr/src/linux/include/linux/fs.h:1701: error: âstruct inodeâ has no member named âi_writecountâ
/usr/src/linux/include/linux/fs.h: In function âallow_write_accessâ:
/usr/src/linux/include/linux/fs.h:1706: error: âstruct dentryâ has no member named âd_inodeâ
/usr/src/linux/include/linux/fs.h: At top level:
/usr/src/linux/include/linux/fs.h:1721: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âfind_inode_numberâ
In file included from /usr/src/linux/include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/usr/src/linux/include/linux/fs.h:1726: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âdefault_llseekâ
/usr/src/linux/include/linux/fs.h:1728: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âvfs_llseekâ
/usr/src/linux/include/linux/fs.h:1733: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âiuniqueâ
/usr/src/linux/include/linux/fs.h: In function âigetâ:
/usr/src/linux/include/linux/fs.h:1753: error: âstruct inodeâ has no member named âi_stateâ
/usr/src/linux/include/linux/fs.h:1754: error: âstruct super_blockâ has no member named âs_opâ
/usr/src/linux/include/linux/fs.h: At top level:
/usr/src/linux/include/linux/fs.h:1791: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h:1791: error: expected declaration specifiers or â...â before âsize_tâ
/usr/src/linux/include/linux/fs.h:1792: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgeneric_file_aio_readâ
/usr/src/linux/include/linux/fs.h:1793: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgeneric_file_aio_writeâ
/usr/src/linux/include/linux/fs.h:1794: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgeneric_file_aio_write_nolockâ
/usr/src/linux/include/linux/fs.h:1796: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgeneric_file_direct_writeâ
/usr/src/linux/include/linux/fs.h:1798: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgeneric_file_buffered_writeâ
/usr/src/linux/include/linux/fs.h:1800: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âdo_sync_readâ
/usr/src/linux/include/linux/fs.h:1801: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âdo_sync_writeâ
/usr/src/linux/include/linux/fs.h:1804: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h:1806: error: expected declaration specifiers or â...â before âsize_tâ
/usr/src/linux/include/linux/fs.h:1809: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgeneric_file_splice_readâ
/usr/src/linux/include/linux/fs.h:1811: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgeneric_file_splice_writeâ
/usr/src/linux/include/linux/fs.h:1813: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgeneric_file_splice_write_nolockâ
/usr/src/linux/include/linux/fs.h:1815: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgeneric_splice_sendpageâ
/usr/src/linux/include/linux/fs.h:1817: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h:1818: error: expected declaration specifiers or â...â before âsize_tâ
/usr/src/linux/include/linux/fs.h:1822: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âno_llseekâ
/usr/src/linux/include/linux/fs.h:1823: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgeneric_file_llseekâ
/usr/src/linux/include/linux/fs.h:1824: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âremote_llseekâ
/usr/src/linux/include/linux/fs.h:1836: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h:1842: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h: In function âdo_generic_file_readâ:
/usr/src/linux/include/linux/fs.h:1846: error: âstruct fileâ has no member named âf_mappingâ
/usr/src/linux/include/linux/fs.h:1847: error: âstruct fileâ has no member named âf_raâ
/usr/src/linux/include/linux/fs.h:1849: error: âpposâ undeclared (first use in this function)
/usr/src/linux/include/linux/fs.h:1851: warning: passing argument 5 of âdo_generic_mapping_readâ from incompatible pointer type
/usr/src/linux/include/linux/fs.h:1851: error: too many arguments to function âdo_generic_mapping_readâ
/usr/src/linux/include/linux/fs.h: At top level:
/usr/src/linux/include/linux/fs.h:1910: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h:1911: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h:1912: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âinode_get_bytesâ
/usr/src/linux/include/linux/fs.h:1913: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h:1929: warning: parameter names (without types) in function declaration
/usr/src/linux/include/linux/fs.h:1934: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âdcache_dir_lseekâ
/usr/src/linux/include/linux/fs.h:1948: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h:1951: error: expected declaration specifiers or â...â before âloff_tâ
/usr/src/linux/include/linux/fs.h:1955: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âgeneric_read_dirâ
/usr/src/linux/include/linux/fs.h:1964: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âsimple_read_from_bufferâ
/usr/src/linux/include/linux/fs.h:1978: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âparent_inoâ
/usr/src/linux/include/linux/fs.h:1998: error: expected specifier-qualifier-list before âssize_tâ
/usr/src/linux/include/linux/fs.h:2005: error: expected declaration specifiers or â...â before âsize_tâ
/usr/src/linux/include/linux/fs.h:2006: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âsimple_transaction_readâ
/usr/src/linux/include/linux/fs.h:2010: error: expected declaration specifiers or â...â before âsize_tâ
/usr/src/linux/include/linux/fs.h: In function âsimple_transaction_setâ:
/usr/src/linux/include/linux/fs.h:2012: error: âstruct fileâ has no member named âprivate_dataâ
/usr/src/linux/include/linux/fs.h:2021: error: âstruct simple_transaction_argrespâ has no member named âsizeâ
/usr/src/linux/include/linux/fs.h:2021: error: ânâ undeclared (first use in this function)
/usr/src/linux/include/linux/fs.h: At top level:
/usr/src/linux/include/linux/fs.h:2061: error: expected declaration specifiers or â...â before âu64â
/usr/src/linux/include/linux/fs.h:2061: error: expected declaration specifiers or â...â before âu64â
/usr/src/linux/include/linux/fs.h:2064: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âsimple_attr_readâ
/usr/src/linux/include/linux/fs.h:2066: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before âsimple_attr_writeâ
/usr/src/linux/include/linux/fs.h:2092: error: expected declaration specifiers or â...â before âsize_tâ
/usr/src/linux/include/linux/fs.h:2092: error: expected declaration specifiers or â...â before âloff_tâ
In file included from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/usr/src/linux/include/linux/poll.h:13:25: error: asm/uaccess.h: No such file or directory
In file included from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/usr/src/linux/include/linux/poll.h: In function âget_fd_setâ:
/usr/src/linux/include/linux/poll.h:95: warning: implicit declaration of function âcopy_from_userâ
/usr/src/linux/include/linux/poll.h:95: error: âEFAULTâ undeclared (first use in this function)
/usr/src/linux/include/linux/poll.h:97: error: too many arguments to function âmemsetâ
/usr/src/linux/include/linux/poll.h: In function âset_fd_setâ:
/usr/src/linux/include/linux/poll.h:105: warning: implicit declaration of function â__copy_to_userâ
/usr/src/linux/include/linux/poll.h: In function âzero_fd_setâ:
/usr/src/linux/include/linux/poll.h:112: error: too many arguments to function âmemsetâ
/usr/src/linux/include/linux/poll.h: At top level:
/usr/src/linux/include/linux/poll.h:117: error: expected declaration specifiers or â...â before âs64â
/usr/src/linux/include/linux/poll.h:119: error: expected declaration specifiers or â...â before âs64â
/usr/src/linux/include/linux/poll.h:119: warning: âstruct pollfdâ declared inside parameter list
In file included from hpetimer.c:30:
/usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/info.h:75: error: expected specifier-qualifier-list before âmode_tâ
In file included from hpetimer.c:31:
/usr/src/linux/include/linux/hpet.h:13: error: expected specifier-qualifier-list before âu64â
hpetimer.c: In function âsnd_hpet_openâ:
hpetimer.c:44: error: expected expression before âunsignedâ
hpetimer.c: In function âhpetimer_initâ:
hpetimer.c:88: error: âEINVALâ undeclared (first use in this function)
make[1]: *** [hpetimer.o] Error 1
make: *** [compile] Error 1

```

please somebody help me... :(

---

