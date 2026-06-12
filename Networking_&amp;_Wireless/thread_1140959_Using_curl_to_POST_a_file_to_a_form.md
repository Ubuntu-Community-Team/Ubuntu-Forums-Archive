---
title: "Using curl to POST a file to a form"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by stickmangumby on 2009-04-28
Looking to simulate a user filling out a form as follows:

```

<form action="" enctype="multipart/form-data" method="post">
<input name="file" type="file" size="40" />
<input name="email" type="text" />
<input name="submit" type="submit" value="submit" />
</form>

```

Using netcat to listen to a manual POST using firefox, I dumped the following:

```

POST / HTTP/1.1
Host: 127.0.0.1
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.9) Gecko/2009042113 Ubuntu/8.04 (hardy) Firefox/3.0.9
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Content-Type: multipart/form-data; boundary=---------------------------2778875461958961895357284724
Content-Length: 493

-----------------------------2778875461958961895357284724
Content-Disposition: form-data; name="file"; filename="test"
Content-Type: application/octet-stream

Testing...

-----------------------------2778875461958961895357284724
Content-Disposition: form-data; name="email"

asd@asd.com
-----------------------------2778875461958961895357284724
Content-Disposition: form-data; name="submit"

submit
-----------------------------2778875461958961895357284724--

```

I've managed to get basically the same using curl by setting --header options, and using the --form option for each form field and the file to be uploaded. The only difference between the output is the Content-Length header, and the string "-----------------------------2778875461958961895357284724". My Content-Length is shorter, and the boundary string appears in hex.

Posting to the actual URL doesn't work - it literally returns gibberish characters to my console, with the string "curl: ( 18 ) transfer closed with 2562 bytes remaining to read" in the middle somewhere.

I am receiving, storing and returning a cookie set by my web server.

I have double checked for javascript in the page containing the form, and am pretty sure there is nothing relevant.

Any pointers as to where I am going wrong? Am I missing something important?

---

