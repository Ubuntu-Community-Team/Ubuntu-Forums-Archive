---
title: "Network config issues. - Proxy settings"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by cracker89 on 2010-11-08
My college providers shifted to a different setting.. I'm not sure what needs to be done. On windows, under the connections tab you need to change the proxy settings and put in the IP address and enter the port to 3000.

Questions: 
1. where lies the linux (ubuntu 10.04) variant to execute the operation.
2. What can be the major obligations of such a change?

I am sure its siimple enough, but I can't get my net to work properly.
The connection provided to the internet is through wireless routers.

---

### Post by cracker89 on 2010-11-08
Ok.. found the network proxy settings. but now things are working except gmail. It says:

```

The connection has timed out

      

      
      
      

      
        
        

          

The server at www.google.com is taking too long to respond.

        


        
        


    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.




        
        
      


      
      

```

Thats what comes on for blocked sites... So I m kind of sure that iits not blocked..
```

**[FONT=Arial][SIZE=10][COLOR=#003333]Nebero[/COLOR][/SIZE][/FONT]  ** 	         	        	        	       [FONT=arial,sans-serif][COLOR=#ffffff]**Access Denied Site Rated :-  PORN**[/COLOR][/FONT] 	       	        	       	      User    	        irshaan320 	       	      Group   	        wifiusers 	       	      Address   	        192.168.1.174 	       	      Url   	        http://www.youtube.com/ 	       	      Policy   	        lab 	       	      Date   	        2010-11-08 04:31:37 pm

```

---

### Post by cracker89 on 2010-11-08
Ok got everything working, except i can acces or open gmail or anything (app,service) connected it.. I had to change the lan proxy server to 192.168.0.200 and connect on port 3000. Post that everything that can be working works. Except gmail. I cant even get a reply on pinging it.. help? I'm using firefox.

---

### Post by SeijiSensei on 2010-11-08
> **cracker89 said:**
> Ok got everything working, except i can acces or open gmail or anything (app,service) connected it.. I had to change the lan proxy server to 192.168.0.200 and connect on port 3000. Post that everything that can be working works. Except gmail. I cant even get a reply on pinging it.. help? I'm using firefox.

Is your university proxying both HTTP and HTTPS (secure) connections on just the former?  Have you had problems reaching other secure servers or just gmail?

---

### Post by cracker89 on 2010-11-08
Just Gmail. I can even log into them. Just gmail has this issue...

---

### Post by cracker89 on 2010-11-08
Request  mod to delte this threaad. Nature of problem seems to have changed.

---

