# libCrypto
Cryptopro lib for Node.js

## Ubuntu

1) Создание контейнера и генерация пары закрытого/открытого ключа в хранилище:

/opt/cprocsp/bin/amd64/csptest -keyset -newkeyset -cont '\\.\HDIMAGE\containerName' -provtype 75 -provider "Crypto-Pro GOST R 34.10-2012 KC1 CSP"

2) Создание запроса на получение сертификата:

/opt/cprocsp/bin/amd64/cryptcp -creatrqst -dn "E=requesteremail@mail.ru, C=RU, CN=localhost, SN=company" -nokeygen -both -ku -cont '\\.\HDIMAGE\containerName' containerName.req

3) Отправить запрос:

http://www.cryptopro.ru/certsrv/

4) Получить сертификат

5) Установить сертификат:

/opt/cprocsp/bin/amd64/certmgr -inst -store umy -file containerName.cer -cont '\\.\HDIMAGE\containerName'


npm install

### Компиляция .so библиотеки

eval \`./setenv.sh --64\`

make -f MakeNodeCryptopro

## Windows

### Компиляция .dll

set PATH=%PATH%C:\Program Files (x86)\Crypto Pro\SDK\include

set INCLUDE=%INCLUDE%C:\Program Files (x86)\Crypto Pro\SDK\include

set LIBPATH=%LIBPATH%C:\Program Files (x86)\Crypto Pro\SDK\lib\amd64

set LIBPATH=%LIBPATH%C:\Program Files (x86)\Crypto Pro\SDK\lib

cl.exe /D_USRDLL /D_WINDLL nodeCryptopro.c /link /DLL /OUT:nodeCryptopro.dll