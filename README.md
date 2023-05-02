# sand_detection
## Detection of sand in wells hackathon Распознавание песка на скважинных данных 

Большая часть мировых запасов углеводородов приходится на долю продуктивных пластов в слабых породах, которые подвержены разрушению. В результате вместе с продуктом добычи из пласта выносит песок, который может быть разного размера: от мельчайшего (до 40 мкм), похожего на пыль, до крупного (700 + мкм), зерна которого можно различить невооруженным глазом. Пескопроявление в скважинах приводит к образованию песчаных пробок и засорению противопесочных фильтров, и в худшем случае, выходу из строя погружных насосов и наземного оборудования скважины. И хотя практически невозможно полностью очистить скважину от песка, детектирование интервалов выноса песка поможет предотвратить ухудшение состояния скважины, тем самым избежав дорогостоящих ремонтно-восстановительных работ.

### Задача 
Разработать модель для автоматического распознавания удара песчинок на акустических данных. 

### Данные 
В задаче хакатона будет использоваться набор данных, который мы получили в лаборатории. Условия при снятии замеров были максимально приближены к реальным условиям скважин: песчинки разных фракций (от 100 мкм до 700 мкм) были подмешаны в поток газа или воды и через маленькое отверстие инжектированы в основной поток, где находился регистрирующий прибор. Скорость чистого потока и с песком была разной: от 10 до 100 м/мин. Частота дискретизации аудио данных составляет 117.2 кГц. Данные можно скачать по ссылке. В папке находятся четыре файла:
train.csv набор данных для обучения 
test.csv набор данных для тестирования 
submission_sample.csv пример файла посылки 
Baseline.ipynb пример решения задачи и генерации файла посылки 

### Метрика 
Баллы за посылку считаются на основе метрики F1 по public выборке тестового датасета. После завершения приема новых посылок баллы каждого участника будут пересчитаны по полной выборке тестового датасета. 

### Формат ввода 
Набор данных train.csv состоит из 300 столбцов data_1, data_2, ..., data_300 с амплитудой аудиосигнала и целевого столбца label, который указывает на наличие удара песчинки в этой аудиозаписи (значение 1) или отсутствие такового (значение 0). 

Аудиозаписи имеют длину от 49 до 300 сигналов. Если длина аудиозаписи меньше 300, то в столбцах с отсутствующими измерениями будет находиться значение NaN. Например, если аудиозапись состоит из 100 сигналов, то столбцы data_1, data_2, ..., data_100 будут содержать значения амплитуд этих сигналов, а столбцы data_101, data_102, ..., data_300 будут содержать значения NaN. 

### Формат вывода 
Решение оформляется в виде файла, содержащего столбец с предсказанным значением label для тестового датасета test.csv. Первая строка файла - название столбца, затем в следующих 450 строках находится по одному числу: 1 или 0. Пример оформления можно посмотреть в файле sample_submission.csv по ссылке.
