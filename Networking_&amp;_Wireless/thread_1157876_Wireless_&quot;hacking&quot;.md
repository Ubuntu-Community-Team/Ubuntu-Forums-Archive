---
title: "Wireless &quot;hacking&quot;"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by jackzam on 2009-05-13
Hey guys out there.

I've just installed Ubuntu on my laptop again, after about ½ years break.

My new interest is to learn how to "hack" wireless network keys?
I've followed some guides, and install some programs, and now im stucked here.

I won't miss-use my skills, i just wan't to extend my knowledge.

so far i've gotten to here:
```
zam@ubuntu:~$ su
Password: 
root@ubuntu:/home/zam# iwpriv
lo        no private ioctls.

eth0      no private ioctls.

wifi0     no private ioctls.

ath0      Available private ioctls :
          setoptie         (8BEE) : set 256 byte  & get   0      
          getoptie         (8BEF) : set   0       & get 256 byte 
          setkey           (8BF2) : set  60 byte  & get   0      
          delkey           (8BF4) : set   7 byte  & get   0      
          setmlme          (8BF0) : set  42 byte  & get   0      
          addmac           (8BF6) : set   1 addr  & get   0      
          delmac           (8BF8) : set   1 addr  & get   0      
          kickmac          (8BFE) : set   1 addr  & get   0      
          wds_add          (8BFA) : set   1 addr  & get   0      
          wds_del          (8BFC) : set   1 addr  & get   0      
          setchanlist      (8BE6) : set  32 byte  & get   0      
          getchanlist      (8BE7) : set   0       & get  32 byte 
          getchaninfo      (8BED) : set   0       & get 2044 byte 
          mode             (8BE2) : set   6 char  & get   0      
          get_mode         (8BE3) : set   0       & get   6 char 
          setwmmparams     (8BE4) : set   4 int   & get   0      
          getwmmparams     (8BE5) : set   3 int   & get   1 int  
          doth_radar       (8BF1) : set   0       & get   0      
          dump_hal_map     (8BF5) : set   0       & get   0      
          cwmin            (0001) : set   3 int   & get   0      
          get_cwmin        (0001) : set   2 int   & get   1 int  
          cwmax            (0002) : set   3 int   & get   0      
          get_cwmax        (0002) : set   2 int   & get   1 int  
          aifs             (0003) : set   3 int   & get   0      
          get_aifs         (0003) : set   2 int   & get   1 int  
          txoplimit        (0004) : set   3 int   & get   0      
          get_txoplimit    (0004) : set   2 int   & get   1 int  
          acm              (0005) : set   3 int   & get   0      
          get_acm          (0005) : set   2 int   & get   1 int  
          noackpolicy      (0006) : set   3 int   & get   0      
          get_noackpolicy  (0006) : set   2 int   & get   1 int  
          setparam         (8BE0) : set   2 int   & get   0      
          getparam         (8BE1) : set   1 int   & get   1 int  
          authmode         (0003) : set   1 int   & get   0      
          get_authmode     (0003) : set   0       & get   1 int  
          protmode         (0004) : set   1 int   & get   0      
          get_protmode     (0004) : set   0       & get   1 int  
          mcastcipher      (0005) : set   1 int   & get   0      
          get_mcastcipher  (0005) : set   0       & get   1 int  
          mcastkeylen      (0006) : set   1 int   & get   0      
          get_mcastkeylen  (0006) : set   0       & get   1 int  
          ucastciphers     (0007) : set   1 int   & get   0      
          get_uciphers     (0007) : set   0       & get   1 int  
          ucastcipher      (0008) : set   1 int   & get   0      
          get_ucastcipher  (0008) : set   0       & get   1 int  
          ucastkeylen      (0009) : set   1 int   & get   0      
          get_ucastkeylen  (0009) : set   0       & get   1 int  
          keymgtalgs       (0015) : set   1 int   & get   0      
          get_keymgtalgs   (0015) : set   0       & get   1 int  
          rsncaps          (0016) : set   1 int   & get   0      
          get_rsncaps      (0016) : set   0       & get   1 int  
          hostroaming      (000C) : set   1 int   & get   0      
          get_hostroaming  (000C) : set   0       & get   1 int  
          privacy          (000D) : set   1 int   & get   0      
          get_privacy      (000D) : set   0       & get   1 int  
          countermeasures  (000E) : set   1 int   & get   0      
          get_countermeas  (000E) : set   0       & get   1 int  
          dropunencrypted  (000F) : set   1 int   & get   0      
          get_dropunencry  (000F) : set   0       & get   1 int  
          wpa              (000A) : set   1 int   & get   0      
          get_wpa          (000A) : set   0       & get   1 int  
          driver_caps      (0010) : set   1 int   & get   0      
          get_driver_caps  (0010) : set   0       & get   1 int  
          maccmd           (0011) : set   1 int   & get   0      
          wmm              (0012) : set   1 int   & get   0      
          get_wmm          (0012) : set   0       & get   1 int  
          hide_ssid        (0013) : set   1 int   & get   0      
          get_hide_ssid    (0013) : set   0       & get   1 int  
          ap_bridge        (0014) : set   1 int   & get   0      
          get_ap_bridge    (0014) : set   0       & get   1 int  
          inact            (0017) : set   1 int   & get   0      
          get_inact        (0017) : set   0       & get   1 int  
          inact_auth       (0018) : set   1 int   & get   0      
          get_inact_auth   (0018) : set   0       & get   1 int  
          inact_init       (0019) : set   1 int   & get   0      
          get_inact_init   (0019) : set   0       & get   1 int  
          abolt            (001A) : set   1 int   & get   0      
          get_abolt        (001A) : set   0       & get   1 int  
          dtim_period      (001C) : set   1 int   & get   0      
          get_dtim_period  (001C) : set   0       & get   1 int  
          bintval          (001D) : set   1 int   & get   0      
          get_bintval      (001D) : set   0       & get   1 int  
          bmiss_ms         (004A) : set   1 int   & get   0      
          get_bmiss_ms     (004A) : set   0       & get   1 int  
          bmiss            (0049) : set   1 int   & get   0      
          get_bmiss        (0049) : set   0       & get   1 int  
          doth             (001E) : set   1 int   & get   0      
          get_doth         (001E) : set   0       & get   1 int  
          doth_pwrtgt      (001F) : set   1 int   & get   0      
          get_doth_pwrtgt  (001F) : set   0       & get   1 int  
          doth_reassoc     (0020) : set   1 int   & get   0      
          doth_algo        (003F) : set   1 int   & get   0      
          get_doth_algo    (003F) : set   0       & get   1 int  
          doth_mincom      (0040) : set   1 int   & get   0      
          get_doth_mincom  (0040) : set   0       & get   1 int  
          doth_slcg        (0041) : set   1 int   & get   0      
          get_doth_slcg    (0041) : set   0       & get   1 int  
          doth_sldg        (0042) : set   1 int   & get   0      
          get_doth_sldg    (0042) : set   0       & get   1 int  
          txcont           (0043) : set   1 int   & get   0      
          get_txcont       (0043) : set   0       & get   1 int  
          txcontrate       (0044) : set   1 int   & get   0      
          get_txcontrate   (0044) : set   0       & get   1 int  
          txcontpower      (0045) : set   1 int   & get   0      
          get_txcontpower  (0045) : set   0       & get   1 int  
          dfstestmode      (0046) : set   1 int   & get   0      
          get_dfstestmode  (0046) : set   0       & get   1 int  
          dfscactime       (0047) : set   1 int   & get   0      
          get_dfscactime   (0047) : set   0       & get   1 int  
          dfsexcltim       (0048) : set   1 int   & get   0      
          get_dfsexcltim   (0048) : set   0       & get   1 int  
          compression      (0021) : set   1 int   & get   0      
          get_compression  (0021) : set   0       & get   1 int  
          ff               (0022) : set   1 int   & get   0      
          get_ff           (0022) : set   0       & get   1 int  
          turbo            (0001) : set   1 int   & get   0      
          get_turbo        (0001) : set   0       & get   1 int  
          xr               (0023) : set   1 int   & get   0      
          get_xr           (0023) : set   0       & get   1 int  
          burst            (0024) : set   1 int   & get   0      
          get_burst        (0024) : set   0       & get   1 int  
          doth_chanswitch  (8BE8) : set   2 int   & get   0      
          pureg            (0025) : set   1 int   & get   0      
          get_pureg        (0025) : set   0       & get   1 int  
          ar               (0026) : set   1 int   & get   0      
          get_ar           (0026) : set   0       & get   1 int  
          wds              (0027) : set   1 int   & get   0      
          get_wds          (0027) : set   0       & get   1 int  
          bgscan           (0028) : set   1 int   & get   0      
          get_bgscan       (0028) : set   0       & get   1 int  
          bgscanidle       (0029) : set   1 int   & get   0      
          get_bgscanidle   (0029) : set   0       & get   1 int  
          bgscanintvl      (002A) : set   1 int   & get   0      
          get_bgscanintvl  (002A) : set   0       & get   1 int  
          mcast_rate       (002B) : set   1 int   & get   0      
          get_mcast_rate   (002B) : set   0       & get   1 int  
          coverageclass    (002C) : set   1 int   & get   0      
          get_coveragecls  (002C) : set   0       & get   1 int  
          countryie        (002D) : set   1 int   & get   0      
          get_countryie    (002D) : set   0       & get   1 int  
          scanvalid        (002E) : set   1 int   & get   0      
          get_scanvalid    (002E) : set   0       & get   1 int  
          regclass         (003B) : set   1 int   & get   0      
          get_regclass     (003B) : set   0       & get   1 int  
          dropunenceapol   (003C) : set   1 int   & get   0      
          get_dropunencea  (003C) : set   0       & get   1 int  
          shpreamble       (003D) : set   1 int   & get   0      
          get_shpreamble   (003D) : set   0       & get   1 int  
          rssi11a          (002F) : set   1 int   & get   0      
          get_rssi11a      (002F) : set   0       & get   1 int  
          rssi11b          (0030) : set   1 int   & get   0      
          get_rssi11b      (0030) : set   0       & get   1 int  
          rssi11g          (0031) : set   1 int   & get   0      
          get_rssi11g      (0031) : set   0       & get   1 int  
          rate11a_x2       (0032) : set   1 int   & get   0      
          get_rate11a_x2   (0032) : set   0       & get   1 int  
          rate11b_x2       (0033) : set   1 int   & get   0      
          get_rate11b_x2   (0033) : set   0       & get   1 int  
          rate11g_x2       (0034) : set   1 int   & get   0      
          get_rate11g_x2   (0034) : set   0       & get   1 int  
          uapsd            (0035) : set   1 int   & get   0      
          get_uapsd        (0035) : set   0       & get   1 int  
          sleep            (0036) : set   1 int   & get   0      
          get_sleep        (0036) : set   0       & get   1 int  
          qosnull          (0037) : set   1 int   & get   0      
          pspoll           (0038) : set   1 int   & get   0      
          eospdrop         (0039) : set   1 int   & get   0      
          get_eospdrop     (0039) : set   0       & get   1 int  
          markdfs          (003A) : set   1 int   & get   0      
          get_markdfs      (003A) : set   0       & get   1 int  
          setiebuf         (8BEA) : set 1032 byte  & get   0      
          getiebuf         (8BE9) : set   0       & get 1032 byte 
          setfilter        (8BEC) : set   4 byte  & get   0      
          rssi_ewma        (004B) : set   1 int   & get   0      
          get_rssi_ewma    (004B) : set   0       & get   1 int  
          debug_draintxq   (004C) : set   1 int   & get   0      
          debug_stopq      (004D) : set   1 int   & get   0      
          debug_txtimeout  (004E) : set   1 int   & get   0      
          debug_athreset   (004F) : set   1 int   & get   0      
          debug_newtxbufs  (0050) : set   1 int   & get   0      
          debug_scanbufs   (0051) : set   1 int   & get   0      
          debug_leaktxbufs (0052) : set   1 int   & get   0      

pan0      no private ioctls.

root@ubuntu:/home/zam# iwpriv wifi0 -forceprism 1
wifi0     no private ioctls.

root@ubuntu:/home/zam# 

```How can i get wifi0 to have some private ioctls?
I use the newest madwifi-driver and i got a Athreos AR5202 wireless card, i think..

Hope you'll help me - thanks in advance
Frederik, Denmark

---

### Post by Sef on 2009-05-13
Locked.  Too much of a potential for misuse.

---

