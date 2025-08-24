# Генерация открытых и закрытых ключей

## Генерация RSA-ключей
Сгенерировать 2048-битный закрытый RSA-ключ и сохранить как KEY1.pem  
`openssl genrsa -out KEY1.pem 2048`

Сгенерировать 4096-битный закрытый RSA-ключ, зашифрованный с помощью AES128  
`openssl genrsa -out KEY2.pem -aes128 4096`

- Размер ключа должен быть последним аргументом команды
- Пропустите аргумент `-out <ФАЙЛ>`, чтобы вывести в стандартный вывод
- Поддерживаются и другие алгоритмы шифрования:
  -aes128, -aes192, -aes256, -des3, -des

## Генерация DSA-ключей:
Сгенерировать файл параметров DSA  
`openssl dsaparam -out DSA-PARAM.pem 1024`

Сгенерировать файл DSA-ключей с использованием файла параметров  
`openssl gendsa -out DSA-KEY.pem DSA-PARAM.pem`

Сгенерировать параметры и ключи DSA в одном файле  
`openssl dsaparam -genkey -out DSA-PARAM-KEY.pem 2048`

*См. раздел проверки для просмотра содержимого файлов.*

---

## Генерация ключей на эллиптических кривых:
Сгенерировать файл параметров EC  
`openssl genpkey -genparam -algorithm EC -pkeyopt ec_paramgen_curve:secp384r1 -out EC-PARAM.pem`

Сгенерировать EC-ключи из файла параметров  
`openssl genpkey -paramfile EC-PARAM.pem -out EC-KEY.pem`

Сгенерировать EC-ключи напрямую  
`openssl genpkey -algorithm EC -pkeyopt ec_paramgen_curve:P-384 -out EC-KEY.pem`

Просмотреть поддерживаемые эллиптические кривые  
`openssl ecparam -list_curves`  
Рекомендуемые кривые: secp521r1, secp384r1, secp256k1 *[эквивалентно P-521, P-384, P-256]*
