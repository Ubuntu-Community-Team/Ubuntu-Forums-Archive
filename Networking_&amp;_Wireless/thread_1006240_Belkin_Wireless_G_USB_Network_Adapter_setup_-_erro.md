---
title: "Belkin Wireless G USB Network Adapter setup - error"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by johndis2000 on 2008-12-09
I am following the instructions to set up my Belkin Wireless G USB Network Adapter (F5D7050B) on the page: [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)")

I followed the instructions up through step 4 with no problems. In step 5, after typing "make clean" and then "make":

john@john-laptop:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make clean
rm -rf *.o *~ .*.cmd *.ko *.mod.c .tmp_versions built-in.o
john@john-laptop:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make

I get the following error: 

make -C /lib/modules/2.6.24-22-generic/build SUBDIRS=/home/john/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-22-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/john/RT73_Linux_STA_Drv1.0.3.6/Module/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/john/RT73_Linux_STA_Drv1.0.3.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
make: *** [all] Error 2

The instructions included this warning about possible errors during this step:

Note: Should you see errors regarding get_wireless_stats during make, open rtmp_main.c in a text editor and find the line #if WIRELESS_EXT >=12, and comment out the line following it, like so:

#if WIRELESS_EXT >= 12
// net_dev->get_wireless_stats = rt73_get_wireless_stats;
net_dev->wireless_handlers = (struct iw_handler_def *) &rt7_iw_handler_def;
#endif

I tried to follow the above instruction, but I'm continuing to get errors after making the changes and trying the "make" command again.
I apparently don't know exactly what to change my rtmp_main.c file to read or if the problem is this CFLAGS thing. Here is the part of the file that I think I need to change, please let me know what it should say instead of this:


#if WIRELESS_EXT >= 12
/*
	========================================================================

	Routine Description:
		get wireless statistics

	Arguments:
		net_dev                     Pointer to net_device

	Return Value:
		struct iw_statistics

	Note:
		This function will be called when query /proc

	========================================================================
*/
long rt_abs(long arg)	{	return (arg<0)? -arg : arg;}
struct iw_statistics *rt73_get_wireless_stats(
	IN  struct net_device *net_dev)
{
	PRTMP_ADAPTER pAd = (PRTMP_ADAPTER) net_dev->priv;

	DBGPRINT(RT_DEBUG_TRACE, "rt73_get_wireless_stats --->\n");

	// TODO: All elements are zero before be implemented

	pAd->iw_stats.status = 0;   // Status - device dependent for now

    pAd->iw_stats.qual.qual = pAd->Mlme.ChannelQuality; // link quality (%retries, SNR, %missed beacons or better...)
#ifdef RTMP_EMBEDDED
    pAd->iw_stats.qual.level = rt_abs(pAd->PortCfg.LastRssi);   // signal level (dBm)
#else
    pAd->iw_stats.qual.level = abs(pAd->PortCfg.LastRssi);      // signal level (dBm)
#endif
	pAd->iw_stats.qual.level += 256 - pAd->BbpRssiToDbmDelta;

    pAd->iw_stats.qual.noise = (pAd->BbpWriteLatch[17] > pAd->BbpTuning.R17UpperBoundG) ? pAd->BbpTuning.R17UpperBoundG : ((ULONG) pAd->BbpWriteLatch[17]); // noise level (dBm)
    pAd->iw_stats.qual.noise += 256 - 143;
	pAd->iw_stats.qual.updated = 1;     // Flags to know if updated

	pAd->iw_stats.discard.nwid = 0;     // Rx : Wrong nwid/essid
	pAd->iw_stats.miss.beacon = 0;      // Missed beacons/superframe

	// pAd->iw_stats.discard.code, discard.fragment, discard.retries, discard.misc has counted in other place

	return &pAd->iw_stats;
}
#endif


Thanks for your help.

---

