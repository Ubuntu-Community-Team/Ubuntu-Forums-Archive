---
title: "3Connect Interface not working in Wine"
date: 2012-09-16
forum: Networking &amp; Wireless
---

### Post by SillySod on 2012-09-16
I have a "3" mobile broadband dongle.  It comes with its own software on the USB stick called "3 Connect".  I have installed it using Wine and it appeared to work.

However, when running I get an error message:

"Error in thread.

Connection not possible.  Please close the application, remove the modem, re-insert the modem, and restart the application.

WIN32 Exception ( 3,221,225,477 ): Access violation.  In thread: 0x0000003B"

The application does load after this message, but the status message always says "Initialising" and it never gets any further.

It works fine under Windows, shortly after the "Initialising" message is displayed, I get "No network" if the dongle isn't plugged in, so it isn't necessary to have the dongle connected before running 3 Connect.

Any ideas how I can get it to work in Ubuntu with Wine?

---

### Post by SillySod on 2012-09-16
I have just remembered (after trying to install 3Connect on a different Ubuntu box) that there was an installation error as follows:

An error occurred while installing the Route Manager - Error code: -2147023898

Hope someone can help!

---

### Post by SillySod on 2013-01-21
I found a workaround.  What I was trying to do was read text messages (and voice messages I suppose but nobody has sent one) from the SIM card in my 3-dongle.

There's no problem in Ubuntu with using the dongle for mobile broadband internet, it was just that the supplied software didn't work which had a facility to retrieve and send SMS messages.

I can use Gammu and Wammu to read the messages, that works a treat.

To send a message, I have registered the telephone number of the SIM card in Skype so I can send a text message with Skype and have the SIM card number show up at the recipient's end.  If they reply on that number then I can read the message in Wammu.

---

