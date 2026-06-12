---
title: "Suggestion for Ralink drivers on 64 bit Ubuntu (RT3562 in my case)"
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by pullmoll on 2012-12-09
While looking for the cause of serious dropouts, i.e. connection loss and retries, low transfer rates etc. with my Ralink 3062 device, I found a possible reason in how **struct sk_buff** is defined and how it is used in the include file *include/os/rt_linux.h*

Ralink is perhaps not aware of the fact that for 64bit Linux the types of sk_buff->tail and ->end are no longer pointers, but unsigned integers. They are defined as **sk_buff_data_t** in *skbuff.h* and the crucial lines from this header file are the following:

```

#if BITS_PER_LONG > 32
#define NET_SKBUFF_DATA_USES_OFFSET 1
#endif

#ifdef NET_SKBUFF_DATA_USES_OFFSET
typedef unsigned int sk_buff_data_t;
#else
typedef unsigned char *sk_buff_data_t;
#endif

```So for 64 bit Linux, one cannot directly access e.g. **skb->tail** and assume it is a pointer. It rather is an _offset_ to add to **skb->data** to obtain the pointer.

To handle this change correctly, we should change some of the macros in the Ralink drivers header file *include/os/rt_linux.h* and also some lines in the source code, which - despite the macros being available -  access **skb->tail** directly.

First, the macros in *include/os/rt_linux.h* that deal with the packet tail should use the *skbuff.h*-defined inline functions **skb_tail_pointer()** and **skb_set_tail_pointer()** like this:
```

#define GET_OS_PKT_DATATAIL(_pkt) \
    (skb_tail_pointer(RTPKT_TO_OSPKT(_pkt)))

``````

#define SET_OS_PKT_DATATAIL(_pkt, _start, _len) \
    (skb_set_tail_pointer(RTPKT_TO_OSPKT(_pkt), \
     (int)((_start) - GET_OS_PKT_DATAPTR(_pkt)) + (_len)))

```The packet end is also of type **sk_buff_data_t** and as such also has its own macro in *skbuff.h*, which returns the pointer regardless of the value of **NET_SKBUFF_DATA_USES_OFFSET**. Thus the Ralink drivers macro **GET_OS_PKT_END** in *include/os/rt_linux.h* should read:
```

#define GET_OS_PKT_END(_pkt) \
    (skb_end_pointer(RTPKT_TO_OSPKT(_pkt)))

```The piece of code that uses **skb->tail** directly is in *os/linux/rt_linux.c* around line **482**: ```
NdisMoveMemory(skb->tail, pHeader802_3, HdrLen);
``` and ```
NdisMoveMemory(skb->tail, pData, DataSize);
```**Note: With 64 bit Linux these two lines of code move data to an (low) unsigned integer value taken as address (i.e. NULL + nn), where they should be using the offset skb->tail added to the skb->data pointer!** So these two lines should instead read:
```
NdisMoveMemory(GET_OS_PKT_DATATAIL(skb), pHeader802_3, HdrLen);
``` and ```
NdisMoveMemory(GET_OS_PKT_DATATAIL(skb), pData, DataSize);
```I have some more minor, cosmetic changes, which were due to warnings issued by gcc-4.8.0. These changes are taking care of unused local variables
and an assignment of a **const char*** to a **char*** (PSTRING). They are not really important, as opposed to the stuff mentioned above.

With above changes my connections _run without dropouts_ and at the download rate of circa 2MB/s which my internet connection is expected to deliver.

I hope this hint helps my fellow Ubuntu users getting stable WLAN connections.

Jürgen

---

### Post by pullmoll on 2013-01-11
Here'a link to the patch against the DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 archive from Ralink's website:

 [http://pastebin.com/VkUjULJ5](http://pastebin.com/VkUjULJ5)

Jürgen

---

### Post by bananstol on 2013-02-08
Im sorry but how do you apply your patch?

Thanks

---

