---
title: "UUSD from gammu"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by artmind on 2012-03-01
Hi all


I need to send and recieve the answer by ussd using gammu

I'm using this command and nothing has happen 
sudo gammu  getussd *111#


log
```

Entering GSM_DialService
SENDING frametype 0x00/length 0x15/21
41A|54T|2B+|43C|55U|53S|44D|3D=|311|2C,|22"|2A*|311|311|311|23# AT+CUSD=1,"*111#
22"|2C,|311|355|0D                                              ",15.           
1 "AT+CUSD=1,"*111#",15"
2 "+CME ERROR: 100"
RECEIVED frametype 0x00/length 0x28/40
41A|54T|2B+|43C|55U|53S|44D|3D=|311|2C,|22"|2A*|311|311|311|23# AT+CUSD=1,"*111#
22"|2C,|311|355|0D |0D |0A |2B+|43C|4DM|45E|20 |45E|52R|52R|4FO ",15...+CME ERRO
52R|3A:|20 |311|300|300|0D |0A                                  R: 100..        
Incoming USSD received
Leaving GSM_DialService
Entering GSM_SetIncomingUSSD
Terminating possible incoming USSD
SENDING frametype 0x00/length 0x0A/10
41A|54T|2B+|43C|55U|53S|44D|3D=|322|0D                          AT+CUSD=2.      
1 "AT+CUSD=2"
2 "+CME ERROR: 100"
RECEIVED frametype 0x00/length 0x1D/29
41A|54T|2B+|43C|55U|53S|44D|3D=|322|0D |0D |0A |2B+|43C|4DM|45E AT+CUSD=2...+CME
20 |45E|52R|52R|4FO|52R|3A:|20 |311|300|300|0D |0A               ERROR: 100..   
CME Error 100: "unknown"
Disabling incoming USSD
SENDING frametype 0x00/length 0x0A/10
41A|54T|2B+|43C|55U|53S|44D|3D=|300|0D                          AT+CUSD=0.      
1 "AT+CUSD=0"
2 "OK"
RECEIVED frametype 0x00/length 0x10/16
41A|54T|2B+|43C|55U|53S|44D|3D=|300|0D |0D |0A |4FO|4BK|0D |0A  AT+CUSD=0...OK..
Leaving GSM_SetIncomingUSSD
[Terminating]
[Closing]


```

Please help

---

