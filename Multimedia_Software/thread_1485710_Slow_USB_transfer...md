---
title: "Slow USB transfer.."
date: 2010-05-17
forum: Multimedia Software
---

### Post by Baldrick_NZ on 2010-05-17
Has anyone else noticed how show USB transfer rates are under Lucid?

I find that small files are fine, but try a 200Mb+ file. The first 100Mb seems fine, but then it slows right down. Transfer rates are typically 15mB/s to start with, but decrease to around 1.2Mb/s.

Then, right at the last second or so, it seems to just 'hang' for around 20-30 seconds before the file transfer completes.

I use mainly audio files, but have noticed it previously while transferring Ubuntu LiveCD .iso files as well.

Can anyone else verify this? If so, is there a fix/workaround for this issue?

Cheers,
Baldrick.

---

### Post by snakerdlk on 2010-06-01
I have had this problem too.

It seems that the transfer is made through a buffer(hence the great speed at the beginning of the transfer). The buffer then transfers to the device.

But apparently the buffer is filled after some time and the transfer to the buffer now depends on the output of the buffer  to the device, which is slower.

It also explains, that when the file dialog has reached completion, the buffer is still full and must wait until all data remaining in the buffer is written to the device.

---

### Post by it_fixxer on 2010-06-10
Read the following. It can get a bit indepth but it does work. Make sure you read the two links at the end.

[http://ubuntuforums.org/showpost.php?p=8124833&postcount=294](http://ubuntuforums.org/showpost.php?p=8124833&postcount=294)

hope it helps

---

