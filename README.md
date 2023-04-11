# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #4 выполнил(а):
- Артемьев Петр Александрович
- РИ-210950
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы

Ознакомиться с перцептроном

## Задание 1
В новом проекте Unity создала Empty Game Object, навесил на него приложенный к ЛР скрипт.
Обучение перцептрона логическим операциям:
+ OR 
![1](https://user-images.githubusercontent.com/126482589/230717920-b884e846-4b04-4fa5-b9f4-a54e5e71ff9c.png)
![2](https://user-images.githubusercontent.com/126482589/230717928-3a0cbdd1-52a9-4294-8e9b-6d140de7eb5a.png)
+ AND
По сравнению с функцией ИЛИ, для обучения нейрона функции И потребовалось большее количество итераций и соответственно времени.
![3](https://user-images.githubusercontent.com/126482589/230717943-5b17c9d1-4405-4c32-ab42-9abec6375093.png)
+ NAND
![4](https://user-images.githubusercontent.com/126482589/230717956-db884598-cca7-49ff-92ed-dd50326305a4.png)
+ XOR
Даже 100000 итераций было мало для обучения этой функции.
![5](https://user-images.githubusercontent.com/126482589/230717973-333126db-98f0-48ed-affe-e462af10aac9.png)

## Задание 2 Построить графики зависимости количества эпох от ошибки обучения. Указать от чего зависит необходимое количество эпох обучения

На графике отображена зависимость количества ошибок при обучения от количества используемых при обучении итераций. Как видно на диаграмме, XOR - единственная функция, обучение которой не удалось; для остальных функций потребовалось примерно одинаковое количество итераций.

![6](https://user-images.githubusercontent.com/126482589/230717997-9941864c-130a-4e50-b3bf-e874ce3cb04e.png)

Вывод: необходимое количество эпох обучения зависит от смещения (bias) и веса (weight).

```cs
double DotProductBias(double[] v1, double[] v2) 
	{
		if (v1 == null || v2 == null)
			return -1;
	 
		if (v1.Length != v2.Length)
			return -1;
	 
		double d = 0;
		for (int x = 0; x < v1.Length; x++)
		{
			d += v1[x] * v2[x];
		}

		d += bias;
	 
		return d;
	}

	double CalcOutput(int i)
	{
		double dp = DotProductBias(weights,ts[i].input);
		if(dp > 0) return(1);
		return (0);
	}
```

## Задание 3 Построить визуальную модель работы перцептрона на сцене Unity
Скрипт для изменения цвета объекта:

```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ChangeColor : MonoBehaviour
{
    private void OnTriggerEnter(Collider other)
    {
        if (other.gameObject.GetComponent<Renderer>().material.color == Color.white && this.gameObject.GetComponent<Renderer>().material.color == Color.white)
        {
            other.gameObject.GetComponent<Renderer>().material.color = Color.white;
            this.gameObject.GetComponent<Renderer>().material.color = Color.white;
        }
        else
        {
            other.gameObject.GetComponent<Renderer>().material.color = Color.black;
            this.gameObject.GetComponent<Renderer>().material.color = Color.black;
        }
    }
}

```
Черные кубы - 1, белые - 0.
При падении кубы меняют цвет в соответствии с результатом (тестируем логическую функцию ИЛИ)
![7](https://user-images.githubusercontent.com/126482589/230718019-3490e1a5-c718-4174-ae28-bc1f8a22eed7.png)
Результат:
![8](https://user-images.githubusercontent.com/126482589/230718027-1164945a-b331-47e4-9eed-be212f732b90.png)


## Выводы
В ходе данной лабораторной работы, я познакомился с работой перцептрона, изучил процесс обучения логическим операциям, построил графики и изучил зависимость скрорсти обучения от кол-ва эпох.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |
