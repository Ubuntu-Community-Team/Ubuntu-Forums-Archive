---
title: "can't set tx-power with rtl8187 (AWUS036H)"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by manzamanna on 2012-05-03
kernel 3.2.0-24-generic
card Alfa AWUS036H
driver rtl8187

```

# iwconfig wlan1 
wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   **Tx-Power=0 dBm   **
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
# ifconfig wlan1 down
# iw reg set BO
# ifconfig wlan1 up
# iwconfig wlan1 
wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   **Tx-Power=0 dBm   **
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
# iwconfig wlan1 txpower 30
[B]Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan1 ; Invalid argument.[/B]

```

when I change to reg BO dmesg tells:
```

[ 2722.499433] cfg80211: Ignoring regulatory request Set by user since **the driver requires its own regulatory domain to be set first**

```

any hints?
thanks

---

### Post by cawaker on 2012-08-03
i'm running into the exact same problem, the TX power always stays at 0 but the card works, so i'm guessing its just a display issue.

but i've never been able to change the TX power with the  iwconfig wlan1 txpower 30 command.

i think doing the iw reg set BO does the same thing in a different way, but i may be wrong.

---

