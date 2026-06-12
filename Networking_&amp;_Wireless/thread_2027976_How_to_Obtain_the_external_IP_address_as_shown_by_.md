---
title: "?How to Obtain the external IP address as shown by NM applet"
date: 2012-07-17
forum: Networking &amp; Wireless
---

### Post by Neill_R on 2012-07-17
Ubuntu 12.04 server + desktop 

My Internet provider Orange.UK Mobile broadband ICON 225 USB modem. 

The Network manager applet connection information for my HSO0 connection shows the external IP address for my computer.

How can one obtain this information programmatically?

Before ddclient updates my DNS entry [www.my-domain_name.co.uk](www.my-domain_name.co.uk) points at the last value it had and most likely not the current value. accessing a page by 

[http://www.my_domain_name.co.uk/get_address.php](http://www.my_domain_name.co.uk/get_address.php) 

will of course not work. and by 

[http://127.0.0.1/get_address.php](http://127.0.0.1/get_address.php) 

will return 127.0.0.1 from

$ip=$_SERVER[REMOTE_ADDR];

---

### Post by OM55 on 2012-07-17
Here is a small C# code that will give you your public IP. This code uses [http://checkip.dyndns.org](http://checkip.dyndns.org) that returns your public IP.
The function GetExternalIP() will return the string representation of the public IP or "0.0.0.0" in case there is no Internet connection.

Even if you are using a different programming language you should have any problem porting this small function. Basically it interprets the HTML page that is returned and getting out the public IP number.

Hope that helps!


```

using System.Net;
using System.IO;


public string GetExternalIP()
{
    WebClient client  = new WebClient();

    // Add a user agent header in case the requested URI contains a query.
    client.Headers.Add("user-agent", "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.2; .NET CLR1.0.3705;)");

    string baseurl  = "http://checkip.dyndns.org/";
    string s;

    try
    {
        Stream data  = client.OpenRead(baseurl);
        StreamReader reader  = new StreamReader(data);
        s  = reader.ReadToEnd();
        data.Close();
        reader.Close();
        s = s.Replace("<html><head><title>Current IP Check</title></head><body>Current IP Address: ","").Replace("</body></html>","");
        s = s.Substring(0,s.Length-2);
    }
    catch
    {
        s = "0.0.0.0"; // No Internet connection
    }
    return s;
}

```

---

