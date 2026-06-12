---
title: "Dial up access troubleshoting"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by mjtpzfrl on 2009-01-12
To perform a pentesting from the outside into my own dial up computer, i have set up putty to get remote access to it.
      Notice that to make sure having my computer reachable, i performed a pinging which was positive....(my machine is pingable from the outside)...
But i was very surprised to note that i can't reach my dial up machine with putty.
       My question is to know if there is any possibility to be unable to get rootprompt from a dial up computer which is supposed to be not in need of ip or port forwarding..
       There is already several days since iam looking for a suitable response...please help me understand.

THANKS...

---

### Post by superprash2003 on 2009-01-12
try this online port scanner to see if the required port is open [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by mjtpzfrl on 2009-01-12
very thanks for having responded
Your output was very efficient it helped me understanding something
id would like now to ask you very clearly a question
what are all the possibilities which can make an exploit to:
-be unable to give you remote access despite the fact that you  
   use a dial up connection and that the exploit say:
    user@knoppix$ ./sendmail target.com 
                  .....
                  got shell
           after this nothing happens...why..
thanks you

---

### Post by superprash2003 on 2009-01-14
well with ubuntu's default iptables settings as long as there is no service on your machine that is listening to any port , then you are fine!!!

---

