---
title: "using skydrive with ubuntu 9.04 jaunty"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by hihihi100 on 2009-09-10
Hi there:

Does any of you know how to access to skydrive in the current version of Ubuntu? Must I use Wine?

Cheers

---

### Post by mr.suchy on 2009-10-29
I have the same problem. I just found a software to connect to skydrive, google docs. There is one problem, I don't know it's working with wine. Search one the internet software called Gadinet.

Regards!

---

### Post by pointyblue on 2009-10-30
Gladinet doesn't work with Ubuntu/wine - at least it didn't when I tried it a few months ago.

If you make it work please share.

---

### Post by josephuser on 2010-04-26
This doesn't yet work.  Why is it marked [SOLVED]?? Has anyone come up with a solution? If so, please post.  The only thing I can think of is to boot into XP via VirtualBox, link your actual hard drive to the VirtualBox so it can be accessed in the VirtualBox XP, and run it from there.  Otherwise, I don't have any solutions.  

Thoughts?

---

### Post by hihihi100 on 2010-04-27
My mistake, apologizes....

---

### Post by juliobahar on 2010-04-27
> **josephuser said:**
> This doesn't yet work.  Why is it marked [SOLVED]?? Has anyone come up with a solution? If so, please post.  The only thing I can think of is to boot into XP via VirtualBox, link your actual hard drive to the VirtualBox so it can be accessed in the VirtualBox XP, and run it from there.  Otherwise, I don't have any solutions.  

Thoughts?

I do the same thing. Utilize virtualbox WinXp guest to do the job. Still searching for a solution to connect ubuntu to skydrive. Sorry not hope yet. beside internet explorer under WINE isn't helping either.

More thoughts?

---

### Post by pointyblue on 2010-04-28
Perhaps it's possible to map network storage such as gmail or skydrive as a harddrive somehow? Like SDExplorer does in Windows, [http://www.cloudstorageexplorer.com/](http://www.cloudstorageexplorer.com/)

Any idea how?

---

### Post by bionandojr on 2010-06-05
Saudações.
Li uma dúvida igual a sua em um dos Fóruns do Ubuntu. Não lembro o link, mas dizia que é possível acessar o Skydrive no Linux montando o drive virtual como uma partição WebDAV. Para isso, basta usar o programa do seguinte endereço:
 
[http://skydrivesimpleviewer.codeplex.com/releases/view/39728](http://skydrivesimpleviewer.codeplex.com/releases/view/39728)
 
O programa, que roda no Windows e exige Microsoft.NET 3.5 SP1, é bem simples: faz-se o login na plataforma Live e ele retorna o endereço das pastas disponíveis. Para outras informações, veja este endereço:
 
[http://www.winsupersite.com/win7/totw/skydrive2.asp](http://www.winsupersite.com/win7/totw/skydrive2.asp)
 
Vou tentar fazer o teste com o Skydrive depois. Afinal, é bem mais do que os 2 GB do Ubuntu One!
 
 
Boa sorte!

---

### Post by pointyblue on 2010-06-05
Sounds good, I'll check it out.

Btw, bionandojr's post is in Portugese, use Google Translate if you don't understand.

---

### Post by markofealing on 2010-06-07
This sounds like it will work 

[http://www.thesmespace.com/blog/?tag=skydrive](http://www.thesmespace.com/blog/?tag=skydrive)

---

### Post by andersja on 2010-07-30
So - has anyone successfully mounted or otherwise integrated a Windows Live Skydrive into Ubuntu?

---

### Post by marcio123 on 2010-09-17
Try SMEStorage !!

---

### Post by flitbee on 2010-11-03
I am able to  map a Skydrive URL to a networked folder on Windows 7 using this [tip]("http://www.nirmaltv.com/2010/02/02/how-to-map-skydrive-as-network-drive-in-windows/comment-page-1"). I know it is possible in Win 7.

My Q is - is there a way to map such web folders in Linux? If so I can try and hack out a way to..

---

### Post by jakobb on 2010-11-11
> **flitbee said:**
> I am able to  map a Skydrive URL to a networked folder on Windows 7 using this [tip]("http://www.nirmaltv.com/2010/02/02/how-to-map-skydrive-as-network-drive-in-windows/comment-page-1"). I know it is possible in Win 7.

My Q is - is there a way to map such web folders in Linux? If so I can try and hack out a way to..

Same thing, in Win7 I am connected to:
\\abcdef.docs.live.net@SSL\DavWWWRoot\1234567890abcdef\Documents

My guess is that either it uses samba server which is a microsoft way for connecting

or it uses secure http.

however, Another concern is that my logon is [email]name@msn.com[/email] so I end up with two domains,

msn.com and abcdef.docs.live.net

Anyone smart enough to continue from here?

---

### Post by flitbee on 2010-11-11
> **jakobb said:**
> Another concern is that my logon is [email]name@msn.com[/email] so I end up with two domains,

msn.com and abcdef.docs.live.net



What do you mean? and why is that a concern? abcdef.docs.live.net is only your Skydrive host..

---

### Post by jakobb on 2010-11-12
Yes, the question that arises is then, how can I login with a username that contains "@"

---

### Post by flitbee on 2010-11-12
> **jakobb said:**
> Yes, the question that arises is then, how can I login with a username that contains "@"

\\abcdef.docs.live.net@SSL:

The @ has nothign to do with ur username. It just signifies that this is over SSL. In "abcdef.docs.live.net" the abcdef is unique to your ID. For my ID I would have someother name in place of "abcdef"

---

### Post by superprash2003 on 2010-11-16
any luck on getting skydrive to work with ubuntu?

---

### Post by stevenswall on 2011-12-07
Bump. I'm interested in this functionality because I love redundancy. For those who don't mind which tool they use, I've gotten Spyderoak, Wuala, and Dropbox to work on Ubuntu, though none of these offer anywhere near 25GB of free storage.

---

### Post by rworloma on 2012-01-01
Here is the solution:

[http://www.liberiangeek.net/2011/12/mount-map-microsoft-skydrive-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/12/mount-map-microsoft-skydrive-in-ubuntu-11-10-oneiric-ocelot/)

---

### Post by pointyblue on 2012-01-03
> **rworloma said:**
> Here is the solution:

[http://www.liberiangeek.net/2011/12/mount-map-microsoft-skydrive-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/12/mount-map-microsoft-skydrive-in-ubuntu-11-10-oneiric-ocelot/)

Not really. At 1GB/month it would take more than 2 years to fill your 25GB. Even paying users have to accept their fair use policy.

[http://smestorage.com/?p=static&page=faq#Bandwidth limitations]("http://smestorage.com/?p=static&page=faq#Bandwidth limitations")

---

