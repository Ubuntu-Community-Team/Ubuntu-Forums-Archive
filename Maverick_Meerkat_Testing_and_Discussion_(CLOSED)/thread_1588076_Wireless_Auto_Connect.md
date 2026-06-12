---
title: "Wireless Auto Connect"
date: 2010-10-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Weaselpants on 2010-10-04
10.10 wireless does not automatically re-connect after a reboot or when returning from hibernation.  I gave to manually connect.  I'm assuming this is not the correct behavior.  Any ideas?  It's a PITA.

---

### Post by davrosuk on 2010-10-04
You need to make sure "connect automatically" is checked in Preferences -> Network Connections

---

### Post by Weaselpants on 2010-10-04
There is no "connect automatically" option in Network connections.

---

### Post by davrosuk on 2010-10-04
You need to select your connection and edit it to see that option.

---

### Post by Weaselpants on 2010-10-04
davrosuk:  did all that - snooped all the screens.  I don't see any option on any of the screens. More info:  the wireless will not start via ifup -a either.

---

### Post by davrosuk on 2010-10-04
When you edit your wireless connection the check box is right under the connection name - check my screenshot.

---

### Post by Weaselpants on 2010-10-04
Have no clue why I didn't see that - especially after looking at that screen a hundred times.  <sigh>  Turns out it was checked anyway.  Also noticed that there were TWO wireless connections listed - both pointing to the same network.  I changed the name from "Wireless connection 1" to my ssid - evidentally on a restart the system put Wireless connection 1 back in the table so I had two -- System doesn't like that I guess.

Thanks for your help . . .

---

