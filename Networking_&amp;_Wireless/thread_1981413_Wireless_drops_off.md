---
title: "Wireless drops off"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by seastick on 2012-05-16
My wireless connection has taken to bouncing.  It was fine (except that I  was turning off power management each time I started up to solve a  similar problem) and there weren't any updates done to trigger the issue.  It seems very intermittent, and it can be stable for hours.  It has been suggested I try 12.04, but upgrading often seems to cause other issues and all I want is a system I can come to and know it is connected.  Any other suggestions gratefully received.  I'd love to know why it happens too if anyone has any idea.

I'm running Ubuntu 10.04 on an Acer Aspire 5742.  Below is output from commands asked for in Wireless Troubleshooting procedure:


```
 [28556.216011] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28556.218056] wlan0: authenticated
[28556.218086] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28556.222185] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28556.222190] wlan0: associated
[28566.301343] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28566.533064] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28566.732624] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28566.737799] wlan0: direct probe responded
[28566.737804] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28566.740751] wlan0: authenticated
[28566.740775] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28566.744819] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28566.744825] wlan0: associated
[28577.851549] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28578.086377] ath9k: Two wiphys trying to scan at the same time
[28578.086497] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28578.285470] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28578.290643] wlan0: direct probe responded
[28578.290648] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28578.292710] wlan0: authenticated
[28578.292741] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28578.296846] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28578.296850] wlan0: associated
[28589.553142] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28589.756492] ath9k: Two wiphys trying to scan at the same time
[28589.756615] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28589.959118] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28589.964291] wlan0: direct probe responded
[28589.964296] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28589.966278] wlan0: authenticated
[28589.966304] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28589.970428] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28589.970432] wlan0: associated
[28601.106329] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28601.337950] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28601.537669] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28601.542891] wlan0: direct probe responded
[28601.542897] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28601.544891] wlan0: authenticated
[28601.544917] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28601.548945] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28601.548951] wlan0: associated
[28605.384270] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28605.589256] ath9k: Two wiphys trying to scan at the same time
[28605.589379] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28605.790645] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28605.795800] wlan0: direct probe responded
[28605.795807] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28605.797797] wlan0: authenticated
[28605.797825] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28605.801843] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28605.801845] wlan0: associated
[28615.873614] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28616.069093] ath9k: Two wiphys trying to scan at the same time
[28616.268144] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28616.468694] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28616.473775] wlan0: direct probe responded
[28616.473781] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28616.475782] wlan0: authenticated
[28616.475808] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28616.479855] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28616.479861] wlan0: associated
[28627.011333] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28627.246636] ath9k: Two wiphys trying to scan at the same time
[28627.246698] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28627.445760] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28627.450941] wlan0: direct probe responded
[28627.450945] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28627.453006] wlan0: authenticated
[28627.453038] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28627.457083] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28627.457089] wlan0: associated
[28638.037574] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28638.272730] ath9k: Two wiphys trying to scan at the same time
[28638.272955] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28638.471763] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28638.476906] wlan0: direct probe responded
[28638.476912] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28638.478959] wlan0: authenticated
[28638.478995] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28638.483122] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28638.483128] wlan0: associated
[28642.363207] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28642.566596] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28642.767104] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28642.772172] wlan0: direct probe responded
[28642.772177] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28642.774160] wlan0: authenticated
[28642.774181] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28642.778215] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28642.778222] wlan0: associated
[28645.393810] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28645.524352] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28645.743330] ADDRCONF(NETDEV_UP): eth0: link is not ready
[28645.743784] tg3: eth0: Link is down.
[28650.194027] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28651.198060] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28651.198122] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28651.203543] wlan0: direct probe responded
[28651.203550] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28651.205762] wlan0: authenticated
[28651.205812] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28651.209851] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28651.209858] wlan0: associated
[28651.221788] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[28651.570167] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28651.697111] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28651.831431] ADDRCONF(NETDEV_UP): eth0: link is not ready
[28652.084844] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28652.738847] tg3: eth0: Link is down.
[28654.178404] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28654.183064] wlan0: direct probe responded
[28654.183073] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28654.185272] wlan0: authenticated
[28654.185308] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28654.189217] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28654.189224] wlan0: associated
[28654.201355] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[28664.243004] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28664.411450] ath9k: Failed to stop TX DMA in 100 msec after killing last frame
[28664.411480] ath9k: Unable to stop TxDMA. Reset HAL!
[28664.486894] ath9k: Two wiphys trying to scan at the same time
[28664.658741] wlan0: no IPv6 routers present
[28664.689631] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28664.889361] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28664.894518] wlan0: direct probe responded
[28664.894525] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28664.896568] wlan0: authenticated
[28664.896591] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28664.900621] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28664.900626] wlan0: associated
[28674.945425] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28675.184581] ath9k: Two wiphys trying to scan at the same time
[28675.184734] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28675.384094] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28675.389198] wlan0: direct probe responded
[28675.389204] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28675.391192] wlan0: authenticated
[28675.391219] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28675.395256] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28675.395262] wlan0: associated
[28686.051113] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28686.286610] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28686.486562] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28686.491728] wlan0: direct probe responded
[28686.491734] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28686.493721] wlan0: authenticated
[28686.493748] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28686.497777] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28686.497783] wlan0: associated
[28696.981106] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28697.212543] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28697.412899] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28697.418115] wlan0: direct probe responded
[28697.418122] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28697.420187] wlan0: authenticated
[28697.420219] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28697.424324] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28697.424328] wlan0: associated
[28708.039482] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28708.278868] ath9k: Two wiphys trying to scan at the same time
[28708.278958] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28708.310603] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28708.422712] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28708.422823] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28708.436378] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28708.436493] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28708.585252] ADDRCONF(NETDEV_UP): eth0: link is not ready
[28708.708934] tg3: eth0: Link is down.
[28713.161091] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28713.161188] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28713.165813] wlan0: direct probe responded
[28713.165820] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28713.168098] wlan0: authenticated
[28713.168134] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28713.172050] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28713.172056] wlan0: associated
[28713.184120] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[28718.750911] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28718.878167] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28719.009133] ADDRCONF(NETDEV_UP): eth0: link is not ready
[28719.249746] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28719.703684] tg3: eth0: Link is down.
[28721.379151] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28721.383748] wlan0: direct probe responded
[28721.383755] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28721.386014] wlan0: authenticated
[28721.386055] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28721.386549] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28721.386606] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28721.395467] wlan0: direct probe responded
[28721.395472] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28721.397478] wlan0: authenticated
[28721.397509] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28721.401366] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28721.401372] wlan0: associated
[28721.413474] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[28723.312666] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28723.448664] ath9k: Failed to stop TX DMA in 100 msec after killing last frame
[28723.448697] ath9k: Unable to stop TxDMA. Reset HAL!
[28723.535749] ath9k: Two wiphys trying to scan at the same time
[28723.535818] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28723.734723] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28723.739916] wlan0: direct probe responded
[28723.739921] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28723.741966] wlan0: authenticated
[28723.741989] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28723.746104] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28723.746110] wlan0: associated
[28732.347979] wlan0: no IPv6 routers present
[28733.822362] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28734.042644] ath9k: Two wiphys trying to scan at the same time
[28734.042684] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28734.244854] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28734.250060] wlan0: direct probe responded
[28734.250067] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28734.252055] wlan0: authenticated
[28734.252084] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28734.256127] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28734.256133] wlan0: associated
[28745.024310] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28745.255907] ath9k: Two wiphys trying to scan at the same time
[28745.255945] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28745.274463] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28745.375897] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28745.375939] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28745.400540] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28745.400592] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28745.400607] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28745.549694] ADDRCONF(NETDEV_UP): eth0: link is not ready
[28745.689484] tg3: eth0: Link is down.
[28750.144630] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28750.333998] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28750.334050] wlan0: deauthenticating from c0:c1:c0:49:55:9c by local choice (reason=3)
[28750.345392] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[28750.351833] wlan0: direct probe responded
[28750.351839] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[28750.353820] wlan0: authenticated
[28750.353857] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[28750.357886] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[28750.357894] wlan0: associated
[28750.370016] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[28760.538956] wlan0: no IPv6 routers present
[42088.951522] wlan0: deauthenticated from c0:c1:c0:49:55:9c (Reason: 7)
[42090.090850] wlan0: direct probe to AP c0:c1:c0:49:55:9c (try 1)
[42090.096084] wlan0: direct probe responded
[42090.096088] wlan0: authenticate with AP c0:c1:c0:49:55:9c (try 1)
[42090.098099] wlan0: authenticated
[42090.098129] wlan0: associate with AP c0:c1:c0:49:55:9c (try 1)
[42090.102198] wlan0: RX AssocResp from c0:c1:c0:49:55:9c (capab=0x411 status=0 aid=3)
[42090.102206] wlan0: associated
 Release Date: 01/21/2011
 Manufacturer: Acer
 Product Name: Aspire 5742
 Serial Number: LXR4F02356107188BA1601
 Manufacturer: Acer
 Product Name: Aspire 5742
 Serial Number: Base Board Serial Number
 Manufacturer: Acer
 Serial Number: Chassis Serial Number
 Manufacturer: -Virtual Battery 0-
 Manufacture Date: 10/12/2007
 Serial Number: Battery 0
 Manufacturer: OEM_Define2
 Serial Number: OEM_Define3
 Manufacturer: Not Specified
 Serial Number: Not Specified
 Manufacturer: Not Specified
 Serial Number: 43A54E05
 Manufacturer: Intel(R) Corporation
 Serial Number: Not Specified
lo        no wireless extensions.
 eth0      no wireless extensions.
 wlan0     IEEE 802.11bgn  ESSID:"Eastnier"
          Mode:Managed  Frequency:2.462 GHz  Access Point: C0:C1:C0:49:55:9C
          Bit Rate=195 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=30/70  Signal level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq-midi ; : ; }
options ath9k nohwcrypt=1
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
 [main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
21: PCI 100.0: 0200 Ethernet controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_14e4_1692
  Unique ID: rBUF.Ngkfq3qvUy8
  Parent ID: z8Q3.iw_YgxfLCA4
  SysFS ID: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: network
  Model: "Broadcom Ethernet controller"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x1692
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0487
  Revision: 0x01
  Driver: "tg3"
  Driver Modules: "tg3"
  Device File: eth0
  Memory Range: 0xb3400000-0xb340ffff (rw,non-prefetchable)
  IRQ: 28 (3 events)
  HW Address: 1c:75:08:c9:83:70
  Link detected: no
  Module Alias: "pci:v000014E4d00001692sv00001025sd00000487bc02sc00i00"
  Driver Info #0:
    Driver Status: tg3 is active
    Driver Activation Cmd: "modprobe tg3"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #13 (PCI bridge)
 22: PCI 200.0: 0282 WLAN controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_168c_2e
  Unique ID: y9sn.eunzQs34F3D
  Parent ID: qTvu.klt2e4vlFx4
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: network
  Model: "Atheros WLAN controller"
  Vendor: pci 0x168c "Atheros Communications Inc."
  Device: pci 0x002e
  SubVendor: pci 0x105b "Foxconn International, Inc."
  SubDevice: pci 0xe034
  Revision: 0x01
  Driver: "ath9k"
  Driver Modules: "ath9k"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xb2400000-0xb240ffff (rw,non-prefetchable)
  IRQ: 17 (1769718 events)
  HW Address: 90:00:4e:26:31:be
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v0000168Cd0000002Esv0000105Bsd0000E034bc02sc80i00"
  Driver Info #0:
    Driver Status: ath9k is active
    Driver Activation Cmd: "modprobe ath9k"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (PCI bridge)
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
root       926  0.0  0.1  19004  4140 ?        Ssl  10:22   0:07 NetworkManager
root      1018  0.0  0.0   4836  2388 ?        S    10:22   0:07 /sbin/wpa_supplicant -u -s
root      1131  0.2  0.1  25360  6872 ?        S    10:22   1:53 /usr/bin/python -O /usr/share/wicd/daemon/wicd-daemon.py
root      1240  0.0  0.1  12920  7240 ?        S    10:22   0:40 /usr/bin/python -O /usr/share/wicd/daemon/monitor.py
simon     1758  0.0  0.5  35024 19156 ?        S    10:22   0:24 /usr/bin/python -O /usr/share/wicd/gtk/wicd-client.py
simon     5259  0.0  0.0   3320   876 pts/2    S+   22:36   0:00 egrep --color=auto wpa|icd|etwork
root     27635  0.0  0.0   2232  1004 ?        S    18:21   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-wlan0.pid -lf /var/lib/dhcp3/dhclient-08e5c030-18a0-41ef-8f44-891be4922da1-wlan0.lease -cf /var/run/nm-dhclient-wlan0.conf wlan0
Module                  Size  Used by
usbhid                 36206  0
hid                    67288  1 usbhid
aes_i586                7268  1
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1
ppdev                   5259  0
joydev                  8740  0
snd_hda_codec_intelhdmi    11622  1
snd_hda_codec_realtek   203472  1
snd_hda_intel          22165  2
snd_hda_codec          74297  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
fbcon                  35102  71
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
snd_pcm_oss            35308  0
softcursor              1189  1 bitblit
snd_mixer_oss          13746  1 snd_pcm_oss
vga16fb                11385  0
snd_pcm                70918  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0
snd_seq_oss            26722  0
snd_seq_midi            4557  0
arc4                    1153  2
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath9k                 306398  0
i915                  290852  3
snd_timer              19130  2 snd_pcm,snd_seq
drm_kms_helper         29329  1 i915
mac80211              205434  1 ath9k
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   164436  4 i915,drm_kms_helper
snd                    54244  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath                     7611  1 ath9k
uvcvideo               57470  0
videodev               34457  1 uvcvideo
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
soundcore               6620  1 snd
cfg80211              126528  3 ath9k,mac80211,ath
output                  1871  1 video
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63677  0
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
serio_raw               3978  0
intel_agp              24671  2 i915
agpgart                31788  2 drm,intel_agp
led_class               2864  1 ath9k
lp                      7028  0
parport                32635  2 ppdev,lp
usb_storage            40065  0
tg3                   109580  0
ahci                   32712  2
```
simon@simon-Acer5742:~$
 All help gratefully received.

---

### Post by cyboreal on 2012-05-17
when you're having the network problem, run `ifconfig` and `lspci` and post the output from both.

---

### Post by seastick on 2012-05-18
Thanks,  here they are

lspci:
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

ifconfig:
eth0      Link encap:Ethernet  HWaddr 1c:75:08:c9:83:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2523 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:212903 (212.9 KB)  TX bytes:212903 (212.9 KB)

wlan0     Link encap:Ethernet  HWaddr 90:00:4e:26:31:be  
          inet addr:192.168.0.134  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::9200:4eff:fe26:31be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:627550 errors:0 dropped:0 overruns:0 frame:0
          TX packets:314074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:825675122 (825.6 MB)  TX bytes:42414061 (42.4 MB)

Hope this helps.  The randomness of events is very trying.

Thanks for your help

---

### Post by cyboreal on 2012-05-18
I have an Atheros WiFi card and it is working flawlessly in 12.04:

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

Can't say for yours, but it looks like a similar card, so you might find the problem resolved in 12.04.

---

