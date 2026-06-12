---
title: "how to calculate broadcast address"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by jamesbon on 2010-12-13
How do I calculate broadcast adrress
if the address space is 192.168.36.16/28 
then what would be broadcast address.

---

### Post by marin123 on 2010-12-13
its the last ip address in that range. if your network has an address 192.168.36.16/28, then add 15 on the last digit, just like you would add 255 if subnet mask was /24.

so the broadcast address is 192.168.36.31/28

---

### Post by CharlesA on 2010-12-13
Is this a homework question?

---

### Post by jamesbon on 2010-12-13
> **marin123 said:**
> its the last ip address in that range. if your network has an address 192.168.36.16/28, then add 15 on the last digit, just like you would add 255 if subnet mask was /24.

so the broadcast address is 192.168.36.31/28
I understand that all bits would be 1 .But in this case I am not able to understand because 
/28 means first 28 bits are gone.
Then what calculation did you did to reach the broadcast address (i.e. add 15 )
How is this result deduced?

Not a homework problem some one asked in interview and told me this was the question.

---

### Post by CharlesA on 2010-12-13
The normal subnet mask for class C addresses is /24. If you are using /28, it gives you a 255.255.255.240 mask.

256-240 = 16 (which is the range of addresses per subnet).

Subnet address:
192.168.36.0
192.168.36.16
192.168.36.32
192.168.36.50

The broadcast address is always 1 before the next subnet address, so:
192.168.36.15
192.168.36.31
192.168.36.49
192.168.36.65

Hope that makes sense.. I'm not all that good at subnetting.

---

### Post by marin123 on 2010-12-13
> **jamesbon said:**
> I understand that all bits would be 1 .But in this case I am not able to understand because 
/28 means first 28 bits are gone.
Then what calculation did you did to reach the broadcast address (i.e. add 15 )
How is this result deduced?

Not a homework problem some one asked in interview and told me this was the question.

/28 means subnet mask 255.255.255.240. in ipv4 subnet mask has 32 bits, and /28 means first 28 bits are set to 1, so you can address (2^4 - 2 = 14) computers on that network.  -2 stands for: 1 address of the subnetwork (first nuber in that series, ie. 192.168.1.0) and 1 broadcast address (last number of that series, ie. add 2^4 to address of subnetwork: 192.168.1.0 + 15 = 192.168.1.15, this is for subnet mask /28).

if you had "normal" subnet mask 255.255.255.0, then subnet address would be 192.168.1.0, and when added 2^8, you get broadcast address 192.168.1.255.

i hope you understood how i calculated it. if you didnt, feel free to ask :)

---

### Post by gmargo on 2010-12-13
Install the **ipcalc** package.
```

$ ipcalc 192.168.36.16/28
Address:   192.168.36.16        11000000.10101000.00100100.0001 0000
Netmask:   255.255.255.240 = 28 11111111.11111111.11111111.1111 0000
Wildcard:  0.0.0.15             00000000.00000000.00000000.0000 1111
=>
Network:   192.168.36.16/28     11000000.10101000.00100100.0001 0000
HostMin:   192.168.36.17        11000000.10101000.00100100.0001 0001
HostMax:   192.168.36.30        11000000.10101000.00100100.0001 1110
Broadcast: 192.168.36.31        11000000.10101000.00100100.0001 1111
Hosts/Net: 14                    Class C, Private Internet

```

Or the **sipcalc** package.
```

$ sipcalc 192.168.36.16/28
-[ipv4 : 192.168.36.16/28] - 0

[CIDR]
Host address            - 192.168.36.16
Host address (decimal)  - 3232244752
Host address (hex)      - C0A82410
Network address         - 192.168.36.16
Network mask            - 255.255.255.240
Network mask (bits)     - 28
Network mask (hex)      - FFFFFFF0
Broadcast address       - 192.168.36.31
Cisco wildcard          - 0.0.0.15
Addresses in network    - 16
Network range           - 192.168.36.16 - 192.168.36.31
Usable range            - 192.168.36.17 - 192.168.36.30

```

---

### Post by jamesbon on 2010-12-13
Yes I now understand this great.Thnx.
Well ipcalc is a good thing but I wanted to brush up my basics.

---

