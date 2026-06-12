---
title: "new java Socket is created more than 3 minutes"
date: 2011-03-07
forum: Networking &amp; Wireless
---

### Post by tulencok on 2011-03-07
Hi everyone

I'm running Ubuntu 10.10. I have a problem with any client side network communication from any java based program/application.  

I've tried to run the following code:

```
 public static void main(String[] args) throws Exception {
        long start = System.currentTimeMillis();
        Socket s = new Socket("ubuntuforums.org", 80);
        System.out.println("1. connection created in "+ (System.currentTimeMillis() - start)/1000.0 + " s");
        s.close();
        start = System.currentTimeMillis();
        s = new Socket("ubuntuforums.org", 80);
        System.out.println("2. connection created in "+ (System.currentTimeMillis() - start)/1000.0 + " s");
        s.close();
    }
```the result is the following:
```
1. connection created in 189.31 s
2. connection created in 0.085 s
```I've tried both java-1.6.0-openjdk and java-6-sun-1.6.0.24 with almost the same results. During the extremely long 189 seconds, the processor is doing almost nothing (java thread has 0 %). I've tried also a wireshark to check what is going on, but the first packet was released after those 189 seconds. There is nothing in log files, I have no exceptions or errors, and the connections work (after the first long delay) just fine.

Any suggestions what to do?

Thanks.

---

### Post by schnepper on 2011-05-06
Try defining the property:

java.net.preferIPv4Stack=true

Some info here: [http://www.thatsjava.com/hotspot-virtual-machine/158534/](http://www.thatsjava.com/hotspot-virtual-machine/158534/)

The bug has been removed:

[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6483406](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6483406)

---

### Post by tulencok on 2011-05-06
Great!

System.setProperty("java.net.preferIPv4Stack","true");

really works! 

How can I set it globally for all java programms? I've tried to insert java.net.preferIPv4Stack=true
in /etc/java-6-sun/net.properties but it didn't work. 

Thanks

---

