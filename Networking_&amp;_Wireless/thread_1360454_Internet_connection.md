---
title: "Internet connection"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by ravijijin on 2009-12-20
How can we connect aircel internet to ubundu
please replay

---

### Post by kiran r on 2010-08-14
If you are using ubuntu version 9.10 or 10.04....its jst matter of getting ur phone connected to ur desktop,and configuring network manager select apn as aircelgprs.com(aircelgprs is enough sometimes) isp no. *99#(if not connected use isp as *99***1#)
If u are using lower versions i suggest u  read the following post it worked for me>>>

These instructions are fairly  generic and should be adaptable to other distros, mobile phones and  mobile networks.

   1. Fire up/install Ubuntu as normal.
   2.  Plug in or enable your Bluetooth adapter. Your Bluetooth adapter will  be automatically detected and drivers loaded - there is nothing for you  to do manually here.
   3. If you have NEVER used Bluetooth on your  Ubuntu setup before, then go to the next step, otherwise skip to Step 11  because you're probably already setup properly.
   4. Get into a  terminal.
   5. Verify that your Bluetooth adapter is running with:
      Code:

      **$ hciconfig -a**

      If you get details  about hci0 listed including manufacturer's name, then your adapter is  working.
      .
   6. Type in the following to edit your  Bluetooth configuration file:
      Code:
[B]
      $ sudo gedit  /etc/bluetooth/hcid.conf[/B]

      This will bring up the Bluetooth  configuration into the GEdit text editor.
      .
   7. Near the  top of the file you will see the following:
      Code:

      [B]#  HCId options
      options {
          # Automatically initialize  new devices
          autoinit yes;

          # Security Manager  mode
          #   none - Security manager disabled
          #   auto -  Use local PIN for incoming connections
          #   user - Always ask  user for a PIN
          #
          security user;[/B]

      Change  the security user line to security auto
      .
   8. A few lines  beneath this is a section that reads as follows:
      Code:

           [B]# Default PIN code for incoming connections
          passkey  "1234";[/B]

      Change the 1234 to something else, eg: 4493. This  is the pin number required for other Bluetooth devices to connect to you  and it would be insecure to leave it at the default.
      .
    9. Save and exit.
  10. Now restart Bluetooth by typing in:
       Code:
[B]
      $ sudo /etc/init.d/bluetooth restart
[/B]
       When you do this, an informational bubble will appear in your task bar  saying <hostname>-0 Device has been made connectable, eg: if your  PC's name is "gordon", the message would say "gordon-0 Device has been  made connectable".
      .
  11. If it isn't enabled already, turn  on Bluetooth on your mobile phone. On a Nokia N95, you bring up the  main menu, then go to Tools->Bluetooth->Change OFF to ON.
  12.  In your terminal, type in the following:
      Code:

      **$  hcitool scan**

      Your PC will now scan for local Bluetooth  devices and your mobile phone should appear in the resulting list after a  few seconds (along with anyone else's Bluetooth-enabled mobile phones  that are in range). The output will look something like:
      Code:

      [B]$ hcitool scan
      Scanning ...
          00:11:22:AA:BB:CC     Nokia N95
      $[/B]

      In this example, my PC has found my  Nokia mobile phone and shown me the MAC address for it.
      .
   13. Highlight and copy the MAC address of the phone to the clipboard  using your mouse and CTRL + SHIFT + C.
  14. Now we need to find the  channel that your phone uses for Dial-Up Networking. Type in:
       Code:

      **$ sdptool browse 00:11:22:AA:BB:CC**

       (Remember to paste, using CTRL + SHIFT + V, the MAC address of YOUR  phone in place of the example above that you copied earlier).
      .
  15. You will see a whole lot of output as the services on your phone  are queried and displayed. Scroll back a bit and look for an entry that  looks similar to the following:
      Code:[B]

      Service  Name: Dial-Up Networking
      Service RecHandle: 0x10022
       Service Class ID List:
        "Dialup Networking" (0x1103)
       Protocol Descriptor List:
        "L2CAP" (0x0100)
         "RFCOMM" (0x0003)
          Channel: 2
      Language Base Attr  List:
        code_ISO639: 0x454e
        encoding:    0x6a
         base_offset: 0x100
      Profile Descriptor List:
         "Dialup Networking" (0x1103)
          Version: 0x0100[/B]

       ...and note down the Channel number. In the case of my Nokia N95, the  channel used is 2.
      .
  16. Now type in:
      Code:
[B]
      sudo gedit /etc/bluetooth/rfcomm.conf[/B]

      Add the  following to the end of the file (NOTE: if you already have an rfcomm0  defined for another device, then simply increment the number, eg:  rfcomm1, for your mobile phone entry):
      Code:
[B]
       rfcomm0 {
              bind no;
              device  00:11:22:AA:BB:CC;
              channel 2;
              comment  "Nokia N95 via Bluetooth";
      }[/B]

      (Remember to paste  down YOUR MAC address and set YOUR channel number as derived from your  phone).
      .
  17. Save and exit.
  18. Now test the  connection to your phone using the following commands:
      Code:
[B]
      $ rfcomm release 0
      $ rfcomm connect 0[/B]

      At  this point, if your phone wasn't paired with Ubuntu already, your phone  will prompt for the PIN number to access Ubuntu and once accepted,  Ubuntu will then prompt you for the mobile phone's PIN. Enter them  accordingly.

      NOTE: If you setup anything other than rfcomm0  earlier, change the number 0 in the connect command to the number of  the device you created, eg: rfcomm1 would mean typing in rfcomm connect 1  instead.

      After a brief delay, you will see the following:
      Code:

      Connected /dev/rfcomm0 to 00:11:22:AA:BB:CC on  channel 2
      Press CTRL-C for hangup

      Hooray! You have  a data connection to your phone, but not to the Internet yet. Press  CTRL + C to break the connection to your mobile.
      .
  19. Now  we need to setup PPP (Point to Point Protocol). This is exactly what  your home ADSL/Cable modem uses to connect to your Internet Provider,  though in our case, the "provider" is aircel. Type in:
      Code:

      [B]$ sudo gedit /etc/ppp/peers/aircel
[/B]
      ...and a blank  file called "aircel" will be created. You can name it anything you  want really, but once created, populate the file with the following:
      Code:

      [B]# aircel PPP initialisation/termination  script
      noauth
      connect "/usr/sbin/chat -v -f  /etc/chatscripts/aircelcn"
      disconnect "/usr/sbin/chat  -v -f /etc/chatscripts/airceldcn"
      silent
       debug
      /dev/rfcomm0
      115200
      defaultroute
       usepeerdns[/B]

      (Remember to change the rfcomm device number  if you're not using zero).

      To reduce the number of messages  going to /var/log/messages, you can remove the "debug" line too.
       .
  20. Save and exit.
  21. Now type in:
      Code:

      **$ sudo gedit /etc/chatscripts/aircelcn**

      ...and  you are presented with another blank file. Populate it with:
       Code:
[B]
      # aircel PPP CONNECT script
      TIMEOUT          5
      ECHO            ON
      ABORT           '\nBUSY\r'
       ABORT           '\nERROR\r'
      ABORT           '\nNO  ANSWER\r'
      ABORT           '\nNO CARRIER\r'
      ABORT            '\nNO DIALTONE\r'
      ABORT            '\nRINGING\r\n\r\nRINGING\r'
      ''              \rAT
       TIMEOUT         12

      OK              ATE1
      OK               'AT+cgdcont=1,"IP","aircelgprs"'
      OK               ATD*99#[/B]

 [U][I](if ur phone shows dialing and then says "subscribe to packet data first"
 u can use aircelgprs.com>aircelgprs 
 *99***1#)[/I][/U]
      .
  22. Save and  close.
  23. Now type in:
      Code:

      [B]$ sudo gedit  /etc/chatscripts/airceldcn
[/B]
      ...and populate the  empty file with:
      Code:

      [B]# aircel PPP DISCONNECT  script
      ABORT        "BUSY"        
      ABORT        "ERROR"        
      ABORT         "NO DIALTONE"    
      SAY        "\nSending break to the modem\n"    
       ""        "\K"        
      ""        "\K"        
      ""        "\K"        
      ""         "+++ATH"    
      ""        "+++ATH"    
      ""        "+++ATH"    
      SAY         "\nPDP context detached\n"
[/B]
  24. Save and exit.
  25. Now we  are ready to rock and/or roll. Let's try and connect to the Internet!  First, let's reconnect to the phone via Bluetooth:
      Code:[B]

      $ rfcomm connect 0[/B]

  26. Once the connection is  established, open up a second terminal window and type in:
       Code:
[B]
      $ pon aircel[/B]
  27. Now let's see if we  picked up the network settings. Type in:
      Code:

      **$  ifconfig**

      ...and you should see an entry similar to the  following:
      Code:

      ppp0      Link  encap point-to-Point Protocol  
                inet  addr:10.120.11.197  P-t-P:10.6.6.6  Mask:255.255.255.255
                 UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
                 RX packets:4 errors:1 dropped:0 overruns:0 frame:0
                 TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
                 collisions:0 txqueuelen:3 
                RX bytes:64 (64.0  B)  TX bytes:97 (97.0 B)

      Yes, we have an IP address!

      NOTE: If you cannot see the entry for "ppp0" in your ifconfig  output, your phone may be taking a little longer to negotiate the  connection. Wait a couple of seconds and try issuing the ifconfig  command again. Failing that, re-issue the pon aircel command and check  ifconfig again. If you still cannot get ppp0 up, it is possible you  might not have data enabled on your phone/plan. Refer to your provider  for assistance, but essentially if you can surf the 'net from your  mobile phone itself, then ppp0 should appear if the rfcomm connection  was successful.

      Anyway, if you can see ppp0, you can now  try and hit the Internet:
      Code:

      $ [B]ping -c4 [www.google.com]("http://www.google.com")
[/B]
      ...and if u get any results thats +ve thats it
      Congratulations -  you've connected to the Internet via your mobile!
      .
  28.  Now bring up Firefox (or other browser) and try and hit a website. If  you get an "offline" error, make sure your browser is not operating in  offline mode. In Firefox, uncheck the "Work Offline" box in the File  menu.
  29. Once you've gotten over how exciting this all is, you  need to disconnect from aircel to ensure you're not going to rack up a  huge phone bill, so go back into the second terminal window and enter:
      Code:

      **$ poff aircel -r**

      ...and this will  automatically break the rfcomm0 connection without needing to press CTRL  + C in the first terminal window.
      .
  30. If you'd like to  automate the commands entered to initiate PPP with your phone, create a  new text file on your desktop (or wherever) as follows:
      Code:

      [B]$ gedit ~/Desktop/connectscript
[/B]
      ...and then  populate the file with the following:
      Code:

       [B]#!/bin/bash
      rfcomm release 0
      rfcomm connect 0 &
      sleep 5
      pon aircel
      read -p "Press Enter to  terminate your session."
      poff aircel[/B]

      This will  simply ensure the rfcomm device is released, then will connect to the  phone, wait for 5 seconds to ensure the connection is up, then start the  PPP to aircel. It will then sit there and wait for you to hit Enter  at which point it will terminate the PPP.
      .
  31. Save and  exit.
  32. Now at the terminal, make the file executable with:
       Code:
[INDENT]      **$ chmod a+x ~/Desktop/connectscript**
[/INDENT]      ...and now you can just double-click on the icon on your desktop,  then Run In Terminal, to connect to your mobile phone in one hit.

      Once finished, issue the poff aircel command again, or hit Enter  in the terminal window running the script above.

---

### Post by kiran r on 2010-08-14
If you are using ubuntu version 9.10 or 10.04....its jst matter of getting ur phone connected to ur desktop,and configuring network manager select apn as aircelgprs.com(aircelgprs is enough sometimes) isp no. *99#(if not connected use isp as *99***1#)
If u are using lower versions i suggest u  read the following post it worked for me>>>

These instructions are fairly  generic and should be adaptable to other distros, mobile phones and  mobile networks.

   1. Fire up/install Ubuntu as normal.
   2.  Plug in or enable your Bluetooth adapter. Your Bluetooth adapter will  be automatically detected and drivers loaded - there is nothing for you  to do manually here.
   3. If you have NEVER used Bluetooth on your  Ubuntu setup before, then go to the next step, otherwise skip to Step 11  because you're probably already setup properly.
   4. Get into a  terminal.
   5. Verify that your Bluetooth adapter is running with:
      Code:

      **$ hciconfig -a**

      If you get details  about hci0 listed including manufacturer's name, then your adapter is  working.
      .
   6. Type in the following to edit your  Bluetooth configuration file:
      Code:
[B]
      $ sudo gedit  /etc/bluetooth/hcid.conf[/B]

      This will bring up the Bluetooth  configuration into the GEdit text editor.
      .
   7. Near the  top of the file you will see the following:
      Code:

      [B]#  HCId options
      options {
      	# Automatically initialize  new devices
      	autoinit yes;

      	# Security Manager  mode
      	#   none - Security manager disabled
      	#   auto -  Use local PIN for incoming connections
      	#   user - Always ask  user for a PIN
      	#
      	security user;[/B]

      Change  the security user line to security auto
      .
   8. A few lines  beneath this is a section that reads as follows:
      Code:

       	# Default PIN code for incoming connections
      	passkey  "1234";

      Change the 1234 to something else, eg: 4493. This  is the pin number required for other Bluetooth devices to connect to you  and it would be insecure to leave it at the default.
      .
    9. Save and exit.
  10. Now restart Bluetooth by typing in:
       Code:
[B]
      $ sudo /etc/init.d/bluetooth restart
[/B]
       When you do this, an informational bubble will appear in your task bar  saying <hostname>-0 Device has been made connectable, eg: if your  PC's name is "gordon", the message would say "gordon-0 Device has been  made connectable".
      .
  11. If it isn't enabled already, turn  on Bluetooth on your mobile phone. On a Nokia N95, you bring up the  main menu, then go to Tools->Bluetooth->Change OFF to ON.
  12.  In your terminal, type in the following:
      Code:

      **$  hcitool scan**

      Your PC will now scan for local Bluetooth  devices and your mobile phone should appear in the resulting list after a  few seconds (along with anyone else's Bluetooth-enabled mobile phones  that are in range). The output will look something like:
      Code:

      [B]$ hcitool scan
      Scanning ...
      	00:11:22:AA:BB:CC	 Nokia N95
      $[/B]

      In this example, my PC has found my  Nokia mobile phone and shown me the MAC address for it.
      .
   13. Highlight and copy the MAC address of the phone to the clipboard  using your mouse and CTRL + SHIFT + C.
  14. Now we need to find the  channel that your phone uses for Dial-Up Networking. Type in:
       Code:

      **$ sdptool browse 00:11:22:AA:BB:CC**

       (Remember to paste, using CTRL + SHIFT + V, the MAC address of YOUR  phone in place of the example above that you copied earlier).
      .
  15. You will see a whole lot of output as the services on your phone  are queried and displayed. Scroll back a bit and look for an entry that  looks similar to the following:
      Code:[B]

      Service  Name: Dial-Up Networking
      Service RecHandle: 0x10022
       Service Class ID List:
        "Dialup Networking" (0x1103)
       Protocol Descriptor List:
        "L2CAP" (0x0100)
         "RFCOMM" (0x0003)
          Channel: 2
      Language Base Attr  List:
        code_ISO639: 0x454e
        encoding:    0x6a
         base_offset: 0x100
      Profile Descriptor List:
         "Dialup Networking" (0x1103)
          Version: 0x0100[/B]

       ...and note down the Channel number. In the case of my Nokia N95, the  channel used is 2.
      .
  16. Now type in:
      Code:
[B]
      sudo gedit /etc/bluetooth/rfcomm.conf[/B]

      Add the  following to the end of the file (NOTE: if you already have an rfcomm0  defined for another device, then simply increment the number, eg:  rfcomm1, for your mobile phone entry):
      Code:
[B]
       rfcomm0 {
              bind no;
              device  00:11:22:AA:BB:CC;
              channel 2;
              comment  "Nokia N95 via Bluetooth";
      }[/B]

      (Remember to paste  down YOUR MAC address and set YOUR channel number as derived from your  phone).
      .
  17. Save and exit.
  18. Now test the  connection to your phone using the following commands:
      Code:
[B]
      $ rfcomm release 0
      $ rfcomm connect 0[/B]

      At  this point, if your phone wasn't paired with Ubuntu already, your phone  will prompt for the PIN number to access Ubuntu and once accepted,  Ubuntu will then prompt you for the mobile phone's PIN. Enter them  accordingly.

      NOTE: If you setup anything other than rfcomm0  earlier, change the number 0 in the connect command to the number of  the device you created, eg: rfcomm1 would mean typing in rfcomm connect 1  instead.

      After a brief delay, you will see the following:
      Code:

      Connected /dev/rfcomm0 to 00:11:22:AA:BB:CC on  channel 2
      Press CTRL-C for hangup

      Hooray! You have  a data connection to your phone, but not to the Internet yet. Press  CTRL + C to break the connection to your mobile.
      .
  19. Now  we need to setup PPP (Point to Point Protocol). This is exactly what  your home ADSL/Cable modem uses to connect to your Internet Provider,  though in our case, the "provider" is Vodafone. Type in:
      Code:

      [B]$ sudo gedit /etc/ppp/peers/aircel
[/B]
      ...and a blank  file called "aircel" will be created. You can name it anything you  want really, but once created, populate the file with the following:
      Code:

      [B]# aircel PPP initialisation/termination  script
      noauth
      connect "/usr/sbin/chat -v -f  /etc/chatscripts/aircelcn"
      disconnect "/usr/sbin/chat  -v -f /etc/chatscripts/airceldcn"
      silent
       debug
      /dev/rfcomm0
      115200
      defaultroute
       usepeerdns[/B]

      (Remember to change the rfcomm device number  if you're not using zero).

      To reduce the number of messages  going to /var/log/messages, you can remove the "debug" line too.
       .
  20. Save and exit.
  21. Now type in:
      Code:

      **$ sudo gedit /etc/chatscripts/aircelcn**

      ...and  you are presented with another blank file. Populate it with:
       Code:
[B]
      # aircel PPP CONNECT script
      TIMEOUT          5
      ECHO            ON
      ABORT           '\nBUSY\r'
       ABORT           '\nERROR\r'
      ABORT           '\nNO  ANSWER\r'
      ABORT           '\nNO CARRIER\r'
      ABORT            '\nNO DIALTONE\r'
      ABORT            '\nRINGING\r\n\r\nRINGING\r'
      ''              \rAT
       TIMEOUT         12

      OK              ATE1
      OK               'AT+cgdcont=1,"IP","aircelgprs"'
      OK               ATD*99#[/B]

 (if ur phone shows dialing and then says "subscribe to packet data first"
 u can use aircelgprs.com>aircelgprs 
 *99***1#)
      .
  22. Save and  close.
  23. Now type in:
      Code:

      [B]$ sudo gedit  /etc/chatscripts/airceldcn
[/B]
      ...and populate the  empty file with:
      Code:

      [B]# aircel PPP DISCONNECT  script
      ABORT		"BUSY"		
      ABORT		"ERROR"		
      ABORT 		"NO DIALTONE"	
      SAY		"\nSending break to the modem\n"	
       ""		"\K"		
      ""		"\K"		
      ""		"\K"		
      ""		 "+++ATH"	
      ""		"+++ATH"	
      ""		"+++ATH"	
      SAY		 "\nPDP context detached\n"
[/B]
  24. Save and exit.
  25. Now we  are ready to rock and/or roll. Let's try and connect to the Internet!  First, let's reconnect to the phone via Bluetooth:
      Code:[B]

      $ rfcomm connect 0[/B]

  26. Once the connection is  established, open up a second terminal window and type in:
       Code:
[B]
      $ pon aircel[/B]
  27. Now let's see if we  picked up the network settings. Type in:
      Code:

      **$  ifconfig**

      ...and you should see an entry similar to the  following:
      Code:

      ppp0      Link  encap:Point-to-Point Protocol  
                inet  addr:10.120.11.197  P-t-P:10.6.6.6  Mask:255.255.255.255
                 UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
                 RX packets:4 errors:1 dropped:0 overruns:0 frame:0
                 TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
                 collisions:0 txqueuelen:3 
                RX bytes:64 (64.0  B)  TX bytes:97 (97.0 B)

      Yes, we have an IP address!

      NOTE: If you cannot see the entry for "ppp0" in your ifconfig  output, your phone may be taking a little longer to negotiate the  connection. Wait a couple of seconds and try issuing the ifconfig  command again. Failing that, re-issue the pon vodafone command and check  ifconfig again. If you still cannot get ppp0 up, it is possible you  might not have data enabled on your phone/plan. Refer to your provider  for assistance, but essentially if you can surf the 'net from your  mobile phone itself, then ppp0 should appear if the rfcomm connection  was successful.

      Anyway, if you can see ppp0, you can now  try and hit the Internet:
      Code:

      $ [B]ping -c4 [www.google.com](www.google.com)
[/B]
      ...and you should get output similar to the following:
       Code:

      PING overclockers.com.au (203.220.0.228) 56(84) bytes  of data.
      64 bytes from chips.ocau.ausgamers.com  (203.220.0.228): icmp_seq=1 ttl=49 time=159 ms
      64 bytes from  chips.ocau.ausgamers.com (203.220.0.228): icmp_seq=2 ttl=49 time=134 ms
      64 bytes from chips.ocau.ausgamers.com (203.220.0.228): icmp_seq=3  ttl=49 time=127 ms
      64 bytes from chips.ocau.ausgamers.com  (203.220.0.228): icmp_seq=4 ttl=49 time=136 ms

      ---  overclockers.com.au ping statistics ---
      4 packets transmitted, 4  received, 0% packet loss, time 3002ms
      rtt min/avg/max/mdev =  25.838/25.885/25.957/0.045 ms
      $

      Congratulations -  you've connected to the Internet via your mobile!
      .
  28.  Now bring up Firefox (or other browser) and try and hit a website. If  you get an "offline" error, make sure your browser is not operating in  offline mode. In Firefox, uncheck the "Work Offline" box in the File  menu.
  29. Once you've gotten over how exciting this all is, you  need to disconnect from aircel to ensure you're not going to rack up a  huge phone bill, so go back into the second terminal window and enter:
      Code:

      **$ poff aircel -r**

      ...and this will  automatically break the rfcomm0 connection without needing to press CTRL  + C in the first terminal window.
      .
  30. If you'd like to  automate the commands entered to initiate PPP with your phone, create a  new text file on your desktop (or wherever) as follows:
      Code:

      [B]$ gedit ~/Desktop/connectscript
[/B]
      ...and then  populate the file with the following:
      Code:

       [B]#!/bin/bash
      rfcomm release 0
      rfcomm connect 0 &
      sleep 5
      pon aircel
      read -p "Press Enter to  terminate your session."
      poff aircel[/B]

      This will  simply ensure the rfcomm device is released, then will connect to the  phone, wait for 5 seconds to ensure the connection is up, then start the  PPP to aircel. It will then sit there and wait for you to hit Enter  at which point it will terminate the PPP.
      .
  31. Save and  exit.
  32. Now at the terminal, make the file executable with:
       Code:

[INDENT]      **$ chmod a+x ~/Desktop/connectscript**
[/INDENT]
      ...and now you can just double-click on the icon on your desktop,  then Run In Terminal, to connect to your mobile phone in one hit.

      Once finished, issue the poff aircel command again, or hit Enter  in the terminal window running the script above.

---

