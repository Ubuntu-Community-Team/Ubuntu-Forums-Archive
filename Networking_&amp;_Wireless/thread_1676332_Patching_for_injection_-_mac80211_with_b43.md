---
title: "Patching for injection - mac80211 with b43"
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by hodginsa on 2011-01-27
Hello everyone,

I've been doing lots of reading on this site and everywhere on the net. I'm trying to patch my b43 driver, and I could not be more confused at the moment. 

The latest patch for mac80211 I found is 2.6.32.2. This is where I get confused, when I search for the file mac80211 on my ubuntu 10.10 computer I find several copies of mac80211.h in several different places. Now I think I need to modify the patch to run it on my version, but the issue is I don't know what to put in. The folders go like this, in no specific order.

/lib/modules/2.6.35-22-generic/...
/lib/modules/2.6.35-24-generic/...
/usr/scr/linux-headers-2.6.35-22/...
/usr/scr/linux-headers-2.6.35-24/...
/usr/scr/linux-headers-2.6.35-22-generic/...
/usr/scr/linux-headers-2.6.35-24-generic/...

This is the patch file here..
```
diff -uNr linux-2.6.32.2/include/net/ieee80211_radiotap.h linux-2.6.32.2-wl_frag-ack/include/net/ieee80211_radiotap.h
--- linux-2.6.32.2/include/net/ieee80211_radiotap.h	2009-12-18 14:27:07.000000000 -0800
+++ linux-2.6.32.2-wl_frag-ack/include/net/ieee80211_radiotap.h	2009-12-19 16:04:22.721448723 -0800
@@ -240,6 +240,9 @@
 						 * retries */
 #define IEEE80211_RADIOTAP_F_TX_CTS	0x0002	/* used cts 'protection' */
 #define IEEE80211_RADIOTAP_F_TX_RTS	0x0004	/* used rts/cts handshake */
+#define IEEE80211_RADIOTAP_F_TX_NOACK	0x0008	/* frame should not be ACKed */
+#define IEEE80211_RADIOTAP_F_TX_NOSEQ	0x0010	/* sequence number handled
+						 * by userspace */
 
 /* Ugly macro to convert literal channel numbers into their mhz equivalents
  * There are certianly some conditions that will break this (like feeding it '30')
diff -uNr linux-2.6.32.2/net/mac80211/tx.c linux-2.6.32.2-wl_frag-ack/net/mac80211/tx.c
--- linux-2.6.32.2/net/mac80211/tx.c	2009-12-18 14:27:07.000000000 -0800
+++ linux-2.6.32.2-wl_frag-ack/net/mac80211/tx.c	2009-12-19 16:12:31.782448438 -0800
@@ -678,6 +678,10 @@
 	u8 *qc;
 	int tid;
 
+	if (unlikely(!(info->flags & IEEE80211_TX_CTL_ASSIGN_SEQ)))
+		return TX_CONTINUE;
+	info->flags &= ~IEEE80211_TX_CTL_ASSIGN_SEQ;
+
 	/*
 	 * Packet injection may want to control the sequence
 	 * number, if we have no matching interface then we
@@ -974,6 +978,12 @@
 			if (*iterator.this_arg & IEEE80211_RADIOTAP_F_FRAG)
 				tx->flags |= IEEE80211_TX_FRAGMENTED;
 			break;
+		case IEEE80211_RADIOTAP_TX_FLAGS:
+			if (*iterator.this_arg & IEEE80211_RADIOTAP_F_TX_NOACK)
+				info->flags |= IEEE80211_TX_CTL_NO_ACK;
+			if (*iterator.this_arg & IEEE80211_RADIOTAP_F_TX_NOSEQ)
+				info->flags &= ~IEEE80211_TX_CTL_ASSIGN_SEQ;
+			break;
 
 		/*
 		 * Please update the file
@@ -1025,6 +1035,8 @@
 	 * it will be cleared/left by radiotap as desired.
 	 */
 	tx->flags |= IEEE80211_TX_FRAGMENTED;
+	/* Same here, controlled by radiotap and the stack */
+	info->flags |= IEEE80211_TX_CTL_ASSIGN_SEQ;
 
 	/* process and remove the injection radiotap header */
 	if (unlikely(info->flags & IEEE80211_TX_CTL_INJECTED)) {
@@ -1088,16 +1100,10 @@
 			return TX_QUEUED;
 	}
 
-	if (is_multicast_ether_addr(hdr->addr1)) {
-		tx->flags &= ~IEEE80211_TX_UNICAST;
+	if (is_multicast_ether_addr(hdr->addr1))
 		info->flags |= IEEE80211_TX_CTL_NO_ACK;
-	} else {
+	else
 		tx->flags |= IEEE80211_TX_UNICAST;
-		if (unlikely(local->wifi_wme_noack_test))
-			info->flags |= IEEE80211_TX_CTL_NO_ACK;
-		else
-			info->flags &= ~IEEE80211_TX_CTL_NO_ACK;
-	}
 
 	if (tx->flags & IEEE80211_TX_FRAGMENTED) {
 		if ((tx->flags & IEEE80211_TX_UNICAST) &&
```

Am I correct that I need to modify its directories to make it work? or is there more to it than that. Where do I need to place the patch file? I seem like I have several choices. 

Am I even doing the correct thing for using injection on my broadcom b4318?

I'm sorry if these are terrible questions, I've been reading several sites and I just feel like I'm going in circles with this. Any help would be great.

I guess I should mention my wireless card currently works wonders on Ubuntu 10.10 with the B43 driver installed. My card is BCM4318. I should also mention I'm doing this to get aircrack-ng to work. 

Thanks to all.

---

### Post by Wolf9466 on 2011-02-02
I'm trying to do the same thing, and have been working on it for about a week, so... *bump*

---

