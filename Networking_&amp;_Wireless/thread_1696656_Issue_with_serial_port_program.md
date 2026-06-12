---
title: "Issue with serial port program"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by alegomaster on 2011-02-27
Hi, right now I am new to Ubuntu so I can't solve this issue by myself.

I wrote a program in C that would communicate data between two computers, and  have an issue with the program. Whenever I sent text from one computer to the other, the recieving computer would send it back to the transmitting computer even though I didn't specify it. Here's the code that is involved with receiving.

```

//First part
file=fopen("/dev/ttyS0","r");
// Some Error checking code

while (1==1)
	{
		while(fgets(test, sizeof(test), file)!=NULL);
		{
		fputs(test, stdout);
		}
        }



```

---

