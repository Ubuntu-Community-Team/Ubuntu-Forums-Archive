---
title: "Getting a TL-WN321G v4 (rt2870) working on Lucid"
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by bibble235 on 2011-04-16
Hi,

Wanted to summarize how to do this in case someone else had the same issue.

I have Lucid 10.04 LTS (32-bit) installed on a compaq F500. Some time ago the wireless switch gave up so I bought a usb wireless thingy. It was a TP-LINK TL-WN321G v4.

So to get this to work I

Downloaded ndiswrapper 1.56 (google ndiswrapper-1.56.tar.gz)
Added 

 wstdcall void* WIN_FUNC(MmGetSystemRoutineAddress,1)
 (struct unicode_string *name)
 {
 struct ansi_string ansi;
 if (RtlUnicodeStringToAnsiString(&ansi, name, TRUE) ==
 STATUS_SUCCESS) {
 WARNING("MmGetSystemRoutineAddress: %s", ansi.buf);
 RtlFreeAnsiString(&ansi);
 }

 return 0;
 }

To ntoskernel.c (this solves ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress')

Patched the ndiswrapper with patch -p0 < iw_ndis.c.diff. Patch is provided below but feel free to google it.

 diff --git a/iw_ndis.c b/iw_ndis.c
 index 434260e..3f5e12c 100644
 --- a/iw_ndis.c
 +++ b/iw_ndis.c
 @@ -1591,6 +1591,12 @@ static int iw_set_auth(struct net_device *dev,
  		if (wrqu->param.value)
  			deauthenticate(wnd);
  		break;
 +	case IW_AUTH_MFP:
 +	        if (wrqu->param.value == IW_AUTH_MFP_DISABLED ||
 +                    wrqu->param.value == IW_AUTH_MFP_OPTIONAL)
 +		        break;
 +		WARNING("MFP not implemented");
 +		return -EOPNOTSUPP;
  	case IW_AUTH_TKIP_COUNTERMEASURES:
  	case IW_AUTH_DROP_UNENCRYPTED:
  	case IW_AUTH_RX_UNENCRYPTED_EAPOL:

This solves ndiswrapper (iw_set_auth:1602): invalid cmd 12

Made the ndiswrapper with make and then make install (as root)

By default ndiswrapper is in /lib/modules/2.6.32-30-generic/kernel/ubuntu/ndiswrapper/ however the install will put it in misc so make a softlink copy or whatever.

Got the drivers for Windows XP TL-WN321G_v4_100611.zip
unzipped and went to the Windows 2000_XP directory

ndiswrapper -i rt2870.inf

And bob should be you uncle

Iain

---

