---
title: "yuvmotionfps"
date: 2010-11-18
forum: Multimedia Software
---

### Post by M4rci on 2010-11-18
Hi,

Can you help me with compiling/installing?

I am getting this error after "make":


tato@tato-WC769AA-AKB-HPE-130cs:~/Desktop/yuvmotionfps-1.6$ make
make  all-recursive
make[1]: Entering directory `/home/tato/Desktop/yuvmotionfps-1.6'
Making all in utils
make[2]: Entering directory `/home/tato/Desktop/yuvmotionfps-1.6/utils'
Making all in mmxsse
make[3]: Entering directory `/home/tato/Desktop/yuvmotionfps-1.6/utils/mmxsse'
if /bin/bash ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../.. -I../../utils    Your  does not even support "i386" for '-march' and '-mcpu'. -g -O2 -pthread -Wall -Wunused -MT build_sub22_mests.lo -MD -MP -MF ".deps/build_sub22_mests.Tpo" \
	  -c -o build_sub22_mests.lo `test -f 'build_sub22_mests.c' || echo './'`build_sub22_mests.c; \
	then mv ".deps/build_sub22_mests.Tpo" ".deps/build_sub22_mests.Plo"; \
	else rm -f ".deps/build_sub22_mests.Tpo"; exit 1; \
	fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../.. -I../../utils Your does not even support i386 for -march and -mcpu. -g -O2 -pthread -Wall -Wunused -MT build_sub22_mests.lo -MD -MP -MF .deps/build_sub22_mests.Tpo -c build_sub22_mests.c  -fPIC -DPIC -o .libs/build_sub22_mests.o
gcc: Your: No such file or directory
gcc: does: No such file or directory
gcc: not: No such file or directory
gcc: even: No such file or directory
gcc: support: No such file or directory
gcc: i386: No such file or directory
gcc: for: No such file or directory
gcc: and: No such file or directory
cc1: error: unrecognized command line option "-march"
cc1: error: unrecognized command line option "-mcpu."
make[3]: *** [build_sub22_mests.lo] Error 1
make[3]: Leaving directory `/home/tato/Desktop/yuvmotionfps-1.6/utils/mmxsse'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tato/Desktop/yuvmotionfps-1.6/utils'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tato/Desktop/yuvmotionfps-1.6'
make: *** [all] Error 2
tato@tato-WC769AA-AKB-HPE-130cs:~/Desktop/yuvmotionfps-1.6$ 


Thank you

---

### Post by aliceinwonderlands on 2010-11-30
Hi,

I had exactly the same error on Maverick 64bits, in my computer the compilation of yuvmotionfps-1.6 worked fine with:

./configure --host=x86_64-pc-linux-gnu

Maybe you could try if this also works for you. I don't really understand why but maybe is because this configure script does not recognize properly the pc architechture (host=x86_64-unkown-linux-gnu) ? Or is because I have something wrong in my instalation ?

Cheers,

---

