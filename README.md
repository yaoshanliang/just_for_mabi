	ssh-keygen -t rsa
	/home/iat/.ssh/id_rsa_yaoshanliang

	
	ssh-keygen -t rsa
	/home/iat/.ssh/id_rsa_1329517386


	ssh-add ~/.ssh/id_rsa_yaoshanliang
	ssh-add ~/.ssh/id_rsa_1329517386
	vim ~/.ssh/config

		#github
		Host github.com
		HostName github.com
		User git
		IdentityFile ~/.ssh/id_rsa
		
		#coding
		Host git.coding.net
		HostName git.coding.net
		User git
		IdentityFile ~/.ssh/id_rsa
		
		#yaoshanliang
		Host yaoshanliang.coding.net
		HostName git.coding.net
		User git
		IdentityFile ~/.ssh/id_rsa_yaoshanliang

		#1329517386
		Host 1329517386.coding.net
		HostName git.coding.net
		User git
		IdentityFile ~/.ssh/id_rsa_1329517386

	cd ~/workspace/Study
	mkdir just_for_mabi
	cd just_for_mabi
	git init
	git remote add yaoshanliang git@yaoshanliang.coding.net:yaoshanliang/just_for_mabi.git
	git remote add 1329517386 git@1329517386.coding.net:1329517386/just_for_mabi.git
	vim run.sh

		#!/bin/bash
		cd /home/iat/workspace/Study/just_for_mabi
		echo `date "+%G-%m-%d %H:%M:%S"`>time
		git add time
		git commit -m 'time'
		git push yaoshanliang master
		git push 1329517386 master	
	
	chmod a+x run.sh

	crontab -e
	0 12 * * * /home/iat/workspace/Study/just_for_mabi/run.sh
	sudo cron restart
