---
title: "Install problem Freeradius"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by fabiofill on 2009-06-19
**I follow this tutorial and have problems.**

##### inicio #######
Partindo do pré-suposto que estão com o Ubuntu 6.06 instalado (padrão com Gnome), vamos para a pasta :

/usr/local/src , onde baixaremos os fontes 

# cd /usr/local/src
# wget [ftp://ftp.freeradius.org/pub/radius/freeradius-1.1.7.tar.gz](ftp://ftp.freeradius.org/pub/radius/freeradius-1.1.7.tar.gz)
# tar -zxvf freeradius-1.1.7.tar.gz
# cd tar freeradius-1.1.7

A instalação padrão não vem com todas as ferramentas "dpkg" instaladas então vamos instalar via apt-get:

# apt-get install dpkg*

O openssl ja esta presente na instalação do Ubuntu mas com algumas dependencias que precisaremos então :

# apt-get build-dep openssl

para a construção dos pacotes .deb (neste caso especifico) precisaremos deixar o compilador bala então rode :

# apt-get build-dep gcc

Também precisaremos desta ferramenta mágica "dpatch" para os patch.

# apt-get install dpatch

O "fakeroot" não pode ficar de fora, heheh
# apt-get install fakeroot

Agora do diretório fonte do freeradius (/usr/local/src/freeradius-1.1.7/)
vamos tentar construir os pacotes .deb, não comentei ainda mas o objetivo de criar os pacotes .deb é porque com estas ferramentas as dependencias são corrigidas mais facilmente, então vamos lá.

# dpkg-buildpackage -rfakeroot 

A primeira saida que tive foi essa :

--------------------------------------------------------------------------------------------
dpkg-buildpackage: source package is freeradius
dpkg-buildpackage: source version is 1.1.7-0
dpkg-buildpackage: source changed by Alan DeKok <aland@freeradius.org>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: dpatch (>= 2) autotools-dev libtool (>= 1.5) libltdl3-dev libpam0g-dev libmysqlclient15-dev | libmysqlclient14-dev | libmysqlclient-dev libgdbm-dev libldap2-dev libsasl2-dev libiodbc2-dev libkrb5-dev libperl-dev snmp libsnmp9-dev | libsnmp5-dev | libsnmp4.2-dev libpq-dev | postgresql-dev libssl-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
--------------------------------------------------------------------------------------------

vocês também devem ter algo parecido, mas nada de pânico, vamos instalar as "bonecas".
Temos que instalar tudo mesmo que não precisamos de suporte a postgre, ldap etc. mas acho mais facil instalar esta lib do que mecher nos arquivos de conf para criar so os .deb que precisaremos. mão a obra e instalem :

# apt-get install autotools-dev
# apt-get install libtool
# apt-get install libltdl3-dev 
# apt-get install libpam0g-dev 
# apt-get install libmysqlclient15-dev 
# apt-get install libgdbm-dev 
# apt-get install libldap2-dev 
# apt-get install libsasl2-dev 
# apt-get install libiodbc2-dev 
# apt-get install libkrb5-dev 
# apt-get install libperl-dev 
# apt-get install snmp 
# apt-get install libsnmp9-dev 
# apt-get install libpq-dev

(eu instalo um por um porque minha conexão é uma merda e se rodar tudo junto não aguento ficar esperando, tambem quando da pau é mais facil de resolver)

Vamos agora rodar novamente o dpkg-buildpackage -rfakeroot

"Ohhh" e a construção dos pacotes foi ...

então no diretório acima de /usr/local/src/freeradius-1.1.7 temos os seguintes pacotes .deb criados:

freeradius-krb5_1.1.7-0_i386.deb
freeradius-ldap_1.1.7-0_i386.deb
freeradius-dialupadmin_1.1.7-0_all.deb 
freeradius-mysql_1.1.7-0_i386.deb
freeradius_1.1.7-0_i386.deb 
freeradius-iodbc_1.1.7-0_i386.deb 
freeradius-postgresql_1.1.7-0_i386.deb

Vamos agora a instalação :
cd ..
então em /usr/local/src 
# dpkg -i freeradius_1.1.7-0_i386.deb

ok ! instalação com sucesso

IMPORTANTE ! 
na instalação atravez do .deb, você tem os arquivos de configuração em /etc/freeradius/ e o script para rodar o radius que é colocado em /etc/init.d não é radiusd e sim freeradius, então para iniciar o radius => /etc/init.d/freeradius start
também será criado um usuário e grupo chamado "freerad"

####### fim ############# 

**When I use the command dpkg-buildpackage -rfakeroot the installation return the message:**

collect2: ld returned 1 exit status
make[5]: ** [radiusd] Error 1
make[5]: Exit directory `/usr/local/src/freeradius-1.1.7/src/main'
make[4]: ** [common] Error 2
make[4]: Exit directory `/usr/local/src/freeradius-1.1.7/src'
make[3]: ** [all] Error 2
make[3]: Exit directory `/usr/local/src/freeradius-1.1.7/src'
make[2]: ** [common] Error 2
make[2]: Exit directory `/usr/local/src/freeradius-1.1.7'
make[1]: ** [all] Error 2
make[1]: Exit directory `/usr/local/src/freeradius-1.1.7'
make: ** [stamp-build] Erro 2
dpkg-buildpackage: falha: debian/rules build gave error exit status 2

**What can I do to resolve my problem??**

---

### Post by jonobr on 2009-06-20
I cant help much but I believe (AFAIK) THere are license issues with openssl and freeradius....
I think if you search the launchpad you will find some related posts, as other people are trying to do this also.

I also notice it appears the package your installing os for 6.06
which is old-ish?

---

