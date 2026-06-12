---
title: "Error in wireless connection"
date: 2012-06-14
forum: Networking &amp; Wireless
---

### Post by livin4th on 2012-06-14
Hello,
            My laptop which has recently been upgraded to 3.2 kernel started  disconnecting to the wireless network since yesterday. I checked the  dmesg and found this. Any suggestins what I should do.

> 
468.519243] iwl4965 0000:0c:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  468.519258] iwl4965 0000:0c:00.0: Loaded firmware version: 228.61.2.24
[  468.519324] iwl4965 0000:0c:00.0: Start IWL Error Log Dump:
[  468.519332] iwl4965 0000:0c:00.0: Status: 0x000213E4, count: 5
[  468.519788] iwl4965 0000:0c:00.0: Desc                                  Time       data1      data2      line
[  468.519802] iwl4965 0000:0c:00.0: FH_ERROR                     (0x000C) 3478849426 0x00000008 0x03530000 208
[  468.519811] iwl4965 0000:0c:00.0: pc      blink1  blink2  ilink1  ilink2  hcmd
[  468.519821] iwl4965 0000:0c:00.0: 0x0046C 0x0A332 0x004C2 0x006DA 0x0A3DE 0x480004E
[  468.519829] iwl4965 0000:0c:00.0: FH register values:
[  468.519894] iwl4965 0000:0c:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X030d4800
[  468.519943] iwl4965 0000:0c:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0030e370
[  468.519990] iwl4965 0000:0c:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000088
[  468.520084] iwl4965 0000:0c:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00819000
[  468.520150] iwl4965 0000:0c:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X0000003c
[  468.520198] iwl4965 0000:0c:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X03530000
[  468.520266] iwl4965 0000:0c:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  468.520330] iwl4965 0000:0c:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0002
[  468.520378] iwl4965 0000:0c:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[  468.522078] ieee80211 phy0: Hardware restart was requested 			 		


---

### Post by yiannis66 on 2012-06-14
Try to boot with the earlier kernel than the one makes  the proplem and see if the proplem is there also.[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/779159]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/779159")

---

