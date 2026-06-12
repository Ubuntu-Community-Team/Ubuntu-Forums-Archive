---
title: "ubuntu beowulf cluster help?"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by robasc on 2009-02-28
I am building a beowulf cluster using the idea created by Tim Brom 

[http://www.calvin.edu/~adams/research/microwulf/sys/microwulf_notes.pdf]("http://www.calvin.edu/~adams/research/microwulf/sys/microwulf_notes.pdf")

I am having difficulty getting nfs to restart. I would also like to say that I am beginner at linux so please be patient with me.

Notice at the bottom is where I left off. this is everything I have completed so far and have come to a dead end.

I have not configured dhcp, pxe, or any ip addresses eth2 automatically connects using dhcp from my router.

Any help would be greatly appreciated. I want to learn this because this cluster is a great learning curve to linux and not to mention this cluster will come in handy to compile large amounts of source code.

OK, here my configuration notes and equipment:

Hardware:

2  GIGABYTE GA-MA74GM-S2 AM2+AM2 AMD 740G MICRO ATX AMD MOTHERBOARD

2  AMD ATHLON 64 X2 520 BRISBANE 2.7GHz SOCKET AM2 65W DUAL-CORE PROCESSOR 

1  SEAGATE BARRACUDA 7200.11 ST31000333AS 1TB 7200 RPM SATA 3.0gb/s HARD DRIVE

2  RAIDMAX HYBRID 2 RX-530-SS 530W ATX12V.2/ EPS12V SLI READY CROSSFIRE POWER SUPPLY

2  G.SKILL 4GB (2 X 2GB) 240-PIN DDR2 SDRAM DDR2 800 (PC2 6400)

2  120 MM CASE FANS

1  LINKSKEY LKV-SO4ASK 4-PORT SLIM PALMTOP PS/2 KVM SWITCH

1  TRENDNET TEG-S80TXE 10/100/1000Mbps COPPER GIGABIT SWITCH

2  LINNKSYS 10/100/1000 GIGAGIT EHTERNET CARDS

1  10/100 ETHERNET CARD

1  DVD/RW DRIVE

5  ETHERNET CABLES

Software:

Head node: Ubuntu Linux 8.10

Node: Ubuntu Server 8.10

OpenMPI


Linux cluster installation:

1: installed Ubuntu Linux on the master node

   Partitions:
   
   /            20003 

   /home        700105

   Swap         1003

   /usr/local   279089

A screenshot of fdisk for partitions:

       Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433       87548   683694270   83  Linux
/dev/sda3           87549       87670      979965   82  Linux swap / Solaris
/dev/sda4           87671      121601   272550757+  83  Linux



2: Installed Ubunutu server on the /usr/local/partition

did not install grub


3: Intall nfs

   3.1: Mounted diskless root partition to  /nodes/nfs/node1 { sudo mkdir -p /nodes/nfs/node1 }
   3.2: Put appropriate entries in /etc/fstab
   3.3: /dev/sda4 /nodes/nfs/node1 ext3 noatime 0 0
   3.4: Run the following command to mount the partitions:  { sudo mount -a } 
   3.5: Install the NFS utilities { sudo apt-get install nfs-common nfs-kernel-server }
   3.6: Configure NFS. Edit /etc/exports, and export the diskless nodes root partitions.
       
         /nodes/nfs/node1 192.168.2.0/24(rw,no_root_squash,sync,no_subtree_check)  
         /nodes           192.168.2.0/24(rw,no_root_squash,sync,no_subtree_check)
         /home            192.168.2.0/24(rw,no_root_squash,sync,no_subtree_check)

   3.7   Restart nfs (/etc/init.d/nfs restart) on the head node

Screenshot of error message displayed:


root@master-node:/home/robert# /etc/init.d/nfs restart
bash: /etc/init.d/nfs: No such file or directory

---

