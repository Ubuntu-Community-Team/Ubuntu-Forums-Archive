---
title: "Intermittent internet over bluetooth"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by datababy on 2010-01-16
I have a laptop running Ubuntu 9.10 with Blueman 1.10 that I would like to have a reliable connection to the internet via my cellphone.
 
The phone is paired, and the connection to rfcomm0 is set up. Sometimes, when I connect, I get a message that the phone goes not support GSM/GPRS and that dial up networking will not work; sometimes I don't.
 
When Ubuntu's network manager goes to dial the connection, I can see the action on my phone. There are two directions that the system can take from here.
 
1) The number is dialed and there is a delay of about as long as one phone ring. The system connects and all is well.
 
2) The number is dialed and there is a delay of 6-7 phone rings. The call is dropped and the system does not connect.
 
I also have two more data points. When I call the number manually/via voice, the system rings 6-7 times (similar to path two) and I get an error message from the service provider. I also own a Nokia device which runs Maemo 5 (a handheld-specific linux distribution). It connects to the internet via the same phone every time (similar to path 1), so I know that the problem is not with the phone or provider.
 
Unfortunately, I dont know how to record the differences between what blueman does when it works, what blueman and network manager do when they don't work and what Maemo does (always works).Does anyone know how to fix this problem?

---

